# Type definitions

- [Variant types](#variant-types)
- [OnFlagMay2019 flags](#onflagmay2019-flags)

## Variant types

```cpp
enum VariantType : uint8_t {
  UNKNOWN,
  FLOAT,
  STRING,
  VECTOR2,
  VECTOR3,
  UNSIGNED,
  SIGNED = 9
}
```

## OnFlagMay2019 flags

```cpp
enum FLagMay {
  ROCK = 1 << 7,
  DUST = 1 << 10,
  FOX = 1 << 11,
  SPACE = 1 << 18,
  MASK = 1 << 19,
  STARTREK = 1 << 21, // 2097408 or 2097168 (?)
  ASSASIN = 1 << 23,
  STREET = 1 << 25,
  RED_PANDA = 1 << 26
}
```
