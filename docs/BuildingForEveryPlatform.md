# Introduction

Greetings, one and all.  Today we shall explore how to build and
deploy a `ggez` game for every possible platform.  For platforms like
Linux and Mac it's pretty darn simple.  For ones like Android it gets
harder and you have to jump through hoops.  The purpose of this is to
document the hoops and give you a cookbook on the best jumping methods
and trajectories.  We will progress generally from the easiest to
hardest jumps.

## Project setup

We will use the `hello_world` example project from ggez for all these
examples.  To do the initial setup, assuming you have cargo installed:

```sh
cargo init --bin 02_hello_world
cd 02_hello_world
```

Now copy-paste the contents of
<https://raw.githubusercontent.com/ggez/ggez/master/examples/02_hello_world.rs>
into `hello_world/src/main.rs`, or just wget it:

```sh
wget https://raw.githubusercontent.com/ggez/ggez/master/examples/02_hello_world.rs
mv hello_world.rs src/main.rs
```

You'll need a font to print "Hello world!" with, so we need to fetch one and
put it in a subdirectory called `resources` in your project root:

```sh
mkdir resources
cd resources
wget https://raw.githubusercontent.com/ggez/ggez/master/resources/DejaVuSerif.ttf
```

Then edit your `Cargo.toml` with your favorite super duper editor and under `[dependencies]` add:

```
ggez = "0.5"
```

Now run `cargo run` and it should build
and run!  ...maybe.  It depends on what platform you're on and what
libraries you have installed.  To make super-duper sure you have all
the bits and pieces in the right places to make this always work, read
on!

# Linux

## Debian

Very easy, just install the required dev packages:

```sh
apt install libasound2-dev libudev-dev pkg-config
```

Then you should be able to build with `cargo run`

## Redhat

Same libraries as Debian, slightly different names.  On CentOS 7 at
least you can install them with:

TODO: Double-check this with 0.5

```sh
yum install alsa-lib-devel
```

## Distributing

TODO: Double-check this with 0.5

You should be able to just copy-paste the executable file and the `resources` directory to wherever you want.

# Mac

Should be able to just install Rust and run the game, same as the basic setup
instructions.

## Distributing

TODO: Fix this now that I have access to a mac.

???

# Windows

TODO: Double-check this with 0.5

Should just build.  We recommend using the MSVC toolchain whenever possible, the MinGW one can be pretty jank and difficult to set up.

## Distributing

Just copy-paste the exe and resource files to the destination computer.

# Android

Not officially supported yet. ;_; See https://github.com/ggez/ggez/issues/70

# iOS

Not officially supported yet. ;_; See https://github.com/ggez/ggez/issues/70

# Web/wasm/emscripten

Not officially supported yet. ;_; See https://github.com/ggez/ggez/issues/71

