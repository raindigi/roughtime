# Building Roughtime

## C++

The Roughtime C++ code is built using [Bazel](https://www.bazel.io/). Everything should build on Linux. On MacOS, `simple_client` should build.

In order to build, install Bazel and run `bazel build ... && bazel test ...`. That should download and build BoringSSL, gTest and Protocol Buffers automatically.

After doing that you should be able to play with `simple_client` by running `./bazel-bin/simple_client roughtime-servers.json`.

### Known Issues

If, on Arch Linux, Bazel complains about the version of Java but you have Java 8 installed, you may need to export `JAVA_HOME=/usr/lib/jvm/java-8-openjdk`.

If you see an error about `_FORTIFY_SOURCE requires compiling with optimization`, pass `--copt=-U_FORTIFY_SOURCE` to Bazel.

## Go

The Roughtime Go code works with `go get`, as is typical for Go code. For example, `go get https://roughtime.googlesource.com/roughtime/go/client` and run `client --servers-file=roughtime/roughtime-servers.json --chain-file=~/roughtime-chain.json`.
