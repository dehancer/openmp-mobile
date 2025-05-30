# OpenMP Mobile

This library provides means to compile and distribute OpenMP library for iOS.

OpenMP is part of [LLVM](https://github.com/llvm/llvm-project) distribution.

## Version

Latest supported version of OpenMP is [16.0.5](https://github.com/llvm/llvm-project/releases/download/llvmorg-16.0.5/openmp-16.0.5.src.tar.xz).

## Supported platforms

- iOS
- iOS Simulator
- tvOS
- tvOS Simulator
- watchOS
- watchOS Simulator
- macOS

## Requirements

- Xcode (including multiple `platforms`)
- LLVM with Clang
- Homebrew
- g++
- CMake
- node
- python
- perl
- ruby (for Cocoapods)
- carthage
- swift

## Why

Libraries such as BLAS, or FAISS depend on OpenMP to run parallel execution across different platforms, this repository is a structured way to get the OpenMP source code compiled and distributed to iOS developers.

## Getting started

Run `./openmp.sh` and it will create `dist/openmp.xcframework` that you can use in your Xcode project.

## openmp.xcframework

Once the compilation is done, you'll have XCframework created with the files below:

```shell
dist/openmp.xcframework
├── Info.plist
├── ios-arm64_arm64e
│   ├── Headers
│   │   ├── omp-tools.h
│   │   ├── omp.h
│   │   └── ompt.h
│   └── libomp.a
├── ios-arm64_arm64e_x86_64-simulator
│   ├── Headers
│   │   ├── omp-tools.h
│   │   ├── omp.h
│   │   └── ompt.h
│   └── libomp.a
├── macos-arm64_arm64e_x86_64
│   ├── Headers
│   │   ├── omp-tools.h
│   │   ├── omp.h
│   │   └── ompt.h
│   └── libomp.a
├── tvos-arm64
│   ├── Headers
│   │   ├── omp-tools.h
│   │   ├── omp.h
│   │   └── ompt.h
│   └── libomp.a
├── tvos-x86_64-simulator
│   ├── Headers
│   │   ├── omp-tools.h
│   │   ├── omp.h
│   │   └── ompt.h
│   └── libomp.a
├── watchos-arm64_32_armv7k
│   ├── Headers
│   │   ├── omp-tools.h
│   │   ├── omp.h
│   │   └── ompt.h
│   └── libomp.a
└── watchos-i386-simulator
    ├── Headers
    │   ├── omp-tools.h
    │   ├── omp.h
    │   └── ompt.h
    └── libomp.a
```

## Takeaways

If you're looking to run parallel code on iOS using Objective-C or Swift, make sure to check `examples` for the details on how to integrate the library.

If you're not looking to run complex calculations (linear algebra, DSP, neural networks), then you might want to consider Apple's Grand Central Dispatch, as it is more optimized to provide a better user experience (battery management and performance).

## Distribution

This package is available using following package managers.

### Swift Package Manager

`./Pacakage.swift` points to remote release hosted on this GitHub repository.
Use [these](https://developer.apple.com/documentation/xcode/adding-package-dependencies-to-your-app) instructions to add this GitHub repository.

### Cocoapods

`./OpenMP.podspec` includes all the specific details about the build.

In your `Podfile` you can add this library using this syntax:

```ruby
pod 'OpenMP', :git => 'https://github.com/eugenehp/openmp-mobile.git', :tag => 'v16.0.5'
```

### Carthage

In `Cartfile` add following:

```ruby
binary "https://raw.githubusercontent.com/eugenehp/openmp-mobile/master/carthage/openmp-static-xcframework.json" ~> 16.0.5
```

## Releases

Release management works using [gh](https://cli.github.com/manual/installation).

```shell
brew install gh tree
```

To release a draft:

```shell
./openmp.sh release
```

## Contributing

Contributions are welcome, feel free to submit an issue or open a pull request.

## License

[MIT](./LICENSE)

Copyright © 2023-2025 [Eugene Hauptmann](http://twitter.com/eugenehp)

## Trademarks

The OpenMP name and the OpenMP logo are registered trademarks of the [OpenMP Architecture Review Board](https://www.openmp.org/about/trademarks/)
