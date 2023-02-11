Angelscript 2.36.0, with clean build process reduced to "just cmake".
For personal use, but do as you please.

## Improvements:

- Better straightforward build with CMake from project's root:

```
cmake . -B ./build
cmake --build ./build
```

- Added CMakeLists for addons
- Added CMake build flag to optionally compile and link addons with library:

```
cmake . -B ./build -DWITH_ADDONS=ON
```
