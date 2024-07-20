# QtBlurHash

A modern Qt/C++ implementation of [BlurHash](https://github.com/woltapp/blurhash). In comparison to other implementations, this uses Qt and modern C++ as much as possible. It also comes with a image provider (for use in QML) and a full test suite.

## Usage

Copy the source files under `src/` into your application. The test suite and image provider are optional and located under `autotests/` and `imageprovider/` respectively.

This requires Qt6 and C++20, but it can be made to compile for C++17 with little changes.

## Credits

* [Nheko's Blurhash](https://github.com/Nheko-Reborn/blurhash) as inspiration and the base for the implementation.
* Tobias Fella for the original image provider.