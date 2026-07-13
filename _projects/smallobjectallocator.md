---
layout: post
title: "Small Object Allocator"
order: 0.5
description: "A modern C++20 small object allocator inspired by Alexandrescu, built around slab allocation, RAII ownership, and measurable memory behavior."
tags: [C++20, Memory Management, Systems Programming, CMake]
role: "Solo Developer"
engine: "C++20 / CMake"
date: 2026-07-13
github_link: "https://github.com/Otoni24/small-object-allocator"
thumbnail: "/assets/images/cover_smallobjectallocator.jpg"
---

Small Object Allocator is a C++20 library designed to efficiently manage frequent allocations of small objects. The project started from Andrei Alexandrescu's classic allocator design and reworks it around a modern, safer API based on RAII and `std::unique_ptr`.

The goal was not simply to reproduce the original implementation, but to understand its low-level memory model and redesign it into a compact library that is easier to integrate into modern C++ code.

```cpp
auto enemy = soa::make_ptr<Enemy>(100, 3.5f);
```

## Technical Highlights

- **Slab-Based Allocation:** Memory is reserved in contiguous slabs divided into fixed-size blocks, reducing repeated calls to the general-purpose heap allocator.
- **Index-Based Free List:** Recycled blocks store the index of the next free block directly inside their own memory, avoiding separate per-block metadata.
- **Lazy Block Initialization:** Fresh blocks are returned sequentially, while only deallocated blocks enter the free list. This avoids pre-initializing every block when a slab is created.
- **Size-Class Dispatch:** Small allocations are routed to dedicated `FixedAllocator` instances according to size and alignment. Unsupported or oversized requests transparently fall back to the standard allocator.
- **RAII Public API:** Objects are created through `soa::make_ptr<T>` and owned by a pointer-sized `soa::Ptr<T>`, implemented as a `std::unique_ptr` with a stateless custom deleter.

## From Alexandrescu to a Modern API

The internal structure preserves the central ideas of Alexandrescu's allocator:

```text
ObjectAllocator
    -> FixedAllocator per size class
        -> multiple Slabs
            -> fixed-size blocks
```

The main changes are in initialization, ownership, and usability.

The original `Chunk` concept is represented here as a `Slab`. Instead of exposing raw allocation or requiring custom `operator new/delete`, the library constructs typed objects directly and returns an owning smart pointer.

This means users do not need to inherit from a special base class, manually pass object sizes, or remember how an object was allocated.

Construction is also exception-safe: if an object's constructor throws, its storage is immediately returned to the allocator.

## Memory Management Decisions

Each slab uses a `std::uint8_t` block index, limiting it to 255 blocks. The value `255` acts as the end-of-list sentinel.

This keeps free-list metadata extremely small, although it also means that very small size classes may use physically smaller slabs than the configured target size.

The allocator uses power-of-two size classes. A request is assigned to the first block size that satisfies both its size and alignment requirements.

For example:

```text
3-byte object  -> 4-byte block
5-byte object  -> 8-byte block
17-byte object -> 32-byte block
```

This creates predictable allocation behavior at the cost of some internal fragmentation near size-class boundaries.

To avoid repeatedly destroying and recreating memory during allocation churn, each size class can retain one completely empty slab for future reuse. Additional empty slabs are released automatically, while `soa::trim()` performs an explicit cleanup pass.

## Lifetime, Statistics, and Debugging

Calling `soa::init()` is optional. Without a custom configuration, the allocator initializes itself lazily on the first allocation.

```cpp
soa::Config config;
config.slabSize = 16 * 1024;
config.keepOneEmptySlabPerSizeClass = true;

soa::init(config);
```

The library tracks both cumulative activity and current allocator state, including:

- Active small and fallback allocations.
- Requested and reserved bytes.
- Total and empty slab counts.
- Allocation and deallocation requests.

These statistics are also used to validate lifetime rules. In debug builds, `soa::shutdown()` detects attempts to destroy the allocator while allocator-owned objects are still alive.

Standard containers can safely store allocator-owned objects through smart pointers:

```cpp
std::vector<soa::Ptr<Enemy>> enemies;
enemies.push_back(soa::make_ptr<Enemy>(100, 3.5f));
```

When the vector is destroyed, each smart pointer returns its object to the allocator automatically.

## Testing & Benchmarks

The project includes focused tests.

Release benchmarks compare `soa::make_ptr` with `std::make_unique` across several object sizes and allocation patterns.

The strongest results appear in repeated allocation/deallocation workloads, where the allocator can reuse existing blocks instead of repeatedly returning to the general-purpose heap. Memory benchmarks also expose the relationship between requested payload and slab-reserved storage.

> **Project Goal:** This project demonstrates low-level C++ memory management, allocator architecture, RAII design, exception safety, performance measurement, and the ability to modernize a classic systems-programming design without hiding its underlying trade-offs.