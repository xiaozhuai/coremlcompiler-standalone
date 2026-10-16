# CoreMLCompiler Standalone

A relocatable build of Apple's `coremlcompiler` that runs **without Xcode being
installed**. The required runtime frameworks are bundled with the package, and
the installed command is named `coremlcompiler-standalone`.

## Source

The executable and bundled frameworks were extracted from **Xcode 26.3
(build 17C529)**. The bundled `coremlcompiler` reports version `3500.32.1` and
its Mach-O build metadata records SDK `26.2`.

## Install

Xcode is not required on the target Mac.

```bash
brew install xiaozhuai/tap/coremlcompiler-standalone
```

## Usage

```bash
coremlcompiler-standalone compile Model.mlpackage OutputDirectory
coremlcompiler-standalone metadata Model.mlpackage
coremlcompiler-standalone version
```

## Integrity and packaging

The release asset contains `Developer` and `SystemFrameworks` beneath
`libexec`. Homebrew Cask downloads and extracts that payload without applying
Formula Mach-O relocation, then creates the command symlink. No Apple binary or
framework is modified or re-signed.

`SHA256SUMS` records the exact original input hashes for independent manual
verification.

## Licensing and modification notice

This tap packages Apple-provided binaries and frameworks extracted from Xcode.
They are not open-source components of this repository and remain subject to
Apple's applicable license terms. Review those terms before using or
redistributing them.

The `coremlcompiler` executable and bundled frameworks are installed without
modification. The tap adds only a symlink named `coremlcompiler-standalone` that
points to the original executable.

The release payload preserves the original `Developer` and `SystemFrameworks`
contents directly beneath `libexec`.

## Notes

- Architectures: `arm64`, `x86_64`
- Verified on macOS 15.7.9 x86_64 and macOS 27.0.1 arm64
- The original Apple code signatures are preserved.
