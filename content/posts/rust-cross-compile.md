---
author: Nekilc
title: Rust cross-compilation on MacOS
date: 2022-03-03
tags: [rust,cross-compilation]
---

## Install toolchain

`brew install filosottile/musl-cross/musl-cross`

## Alias

`ln -s /opt/homebrew/bin/x86_64-linux-musl-gcc /usr/local/bin/musl-gcc`

## Add traget

`rustup target add x86_64-unknown-linux-musl`

## Add flags before cargo command

`RUSTFLAGS="-C linker=x86_64-linux-musl-cc" cargo build --target x86_64-unknown-linux-musl  --release`