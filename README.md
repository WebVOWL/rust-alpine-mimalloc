# `rust-alpine-mimalloc`

Helper script for use in an Alpine Docker image.
Replaces the default musl malloc implementation with [`mimalloc`](https://github.com/microsoft/mimalloc). If you build Rust or C/C++ static executables in an image using this script, the resulting executables will automatically link with `mimalloc` without needing any special build flags.

Supported & tested archs: `amd64`.

## Usage

```docker
RUN git clone "https://github.com/WebVOWL/rust-alpine-mimalloc"

RUN /rust-alpine-mimalloc/build.sh 2.2.4

# Set LD_PRELOAD to use mimalloc globally
ENV LD_PRELOAD=/usr/lib/libmimalloc.so
```

Replace `2.2.4` with your desired version of mimalloc.

## Documentation

The script patches `libc.a`.

For more details, see

- the original [blogpost](https://www.tweag.io/blog/2023-08-10-rust-static-link-with-mimalloc).
- an [offline copy](documentation.html) of the original blogpost.
