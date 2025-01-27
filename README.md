# cargo-xwin

_formerly cargo-xwinbuild_

[![CI](https://github.com/messense/cargo-xwin/workflows/CI/badge.svg)](https://github.com/messense/cargo-xwin/actions?query=workflow%3ACI)
[![Crates.io](https://img.shields.io/crates/v/cargo-xwin.svg)](https://crates.io/crates/cargo-xwin)
[![docs.rs](https://docs.rs/cargo-xwin/badge.svg)](https://docs.rs/cargo-xwin/)
[![PyPI](https://img.shields.io/pypi/v/cargo-xwin.svg)](https://pypi.org/project/cargo-xwin)

Cross compile Cargo project to Windows msvc target with ease. (LLVM installation required.)

**By using this software you are consented to accept the license at [https://go.microsoft.com/fwlink/?LinkId=2086102](https://go.microsoft.com/fwlink/?LinkId=2086102)**

## Installation

```bash
cargo install cargo-xwin
```

You can also install it using pip:

```bash
pip install cargo-xwin
```

## Usage

1. Install [LLVM](https://llvm.org), on macOS: `brew install llvm`
2. Install Rust Windows msvc target via rustup, for example, `rustup target add x86_64-pc-windows-msvc`
3. Run `cargo xwin build`, for example, `cargo xwin build --target x86_64-pc-windows-msvc`

### Run tests with wine

With wine installed, you can run tests with the `cargo xwin test` command,
for example, `cargo xwin test --target x86_64-pc-windows-msvc`

### Customization

The Microsoft CRT and Windows SDK can be customized using the following environment variables or CLI options.

| Environment Variable | CLI option         | Description                                                                                                        |
|----------------------|--------------------|--------------------------------------------------------------------------------------------------------------------|
| `XWIN_ARCH`          | `--xwin-arch`      | The architectures to include, defaults to `x86_64,aarch64`, possible values: x86, x86_64, aarch, aarch64           |
| `XWIN_VARIANT`       | `--xwin-variant`   | The variants to include, defaults to `desktop`, possible values: desktop, onecore, spectre                         |
| `XWIN_VERSION`       | `--xwin-version`   | The version to retrieve, defaults to 16, can either be a major version of 15 or 16, or a `<major>.<minor>` version |
| `XWIN_CACHE_DIR`     | `--xwin-cache-dir` | xwin cache directory to put CRT and SDK files                                                                      |

### CMake Support

Some Rust crates use the [cmake](https://github.com/alexcrichton/cmake-rs) crate to build C/C++ dependencies,
cargo-xwin will generate a [CMake toolchain](https://cmake.org/cmake/help/latest/manual/cmake-toolchains.7.html) file
automatically to make cross compilation work out of the box.

**[ninja](https://ninja-build.org/) is required** to enable CMake support.

## License

This work is released under the MIT license. A copy of the license is provided
in the [LICENSE](./LICENSE) file.
