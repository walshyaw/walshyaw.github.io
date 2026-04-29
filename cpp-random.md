---
title: cpp-java.util.Random
layout: home
nav_order: 6
---

# java.util.Random — C++ Port

---

**Repository:** [https://github.com/walshyaw/cpp-random](https://github.com/walshyaw/cpp-random)

A faithful C++ implementation of Java's `java.util.Random` class, using the same Linear Congruential Generator (LCG) algorithm, constants, and seed transformation as the original Java standard library. Given the same seed, this implementation produces **identical output** to `java.util.Random`.

---

## Algorithm

This implementation uses a **48-bit Linear Congruential Generator** with the following parameters:

| Parameter | Value |
|---|---|
| Multiplier | `0x5DEECE66DL` |
| Addend | `0xBL` |
| Modulus | `2^48` (bitmask `(1L << 48) - 1`) |

The seed transformation on initialization:
```
seed = (seed ^ 0x5DEECE66DL) & ((1L << 48) - 1)
```

Each call to `next(bits)` advances the state and returns the top `bits` bits of the new seed:
```
seed = (seed * 0x5DEECE66DL + 0xBL) & ((1L << 48) - 1)
return (int)(seed >> (48 - bits))
```

---

## API Reference

| Method | Return Type | Description |
|---|---|---|
| `Random(i64 seed)` | — | Constructs and seeds the generator |
| `setSeed(i64 seed)` | `void` | Resets the generator to a new seed |
| `getSeed()` | `i64` | Returns the current internal seed |
| `next(int bits)` | `int` | Core LCG step; returns top `bits` bits |
| `nextInt()` | `int` | Random 32-bit signed integer |
| `nextBytes(vector<ui8>&)` | `void` | Fills a byte vector with random values |
| `nextLong()` | `i64` | Random 64-bit signed integer |
| `nextBoolean()` | `bool` | Random boolean (~50% true) |
| `nextFloat()` | `float` | Random float in `[0.0, 1.0)` |
| `nextDouble()` | `double` | Random double in `[0.0, 1.0)` |
| `nextGaussian()` | `double` | Gaussian-distributed double (mean=0, stddev=1) |

---

## Limitations

- This port does not implement the Java 8+ stream methods (`ints()`, `longs()`, `doubles()`).

---

## Dependencies

- C++17 or later
- `<cmath>` — used by `nextGaussian()` for `std::sqrt` and `std::log`
- `<algorithm>` — used by `nextBytes()` for `std::min`
- `<vector>` — used by `nextBytes()`