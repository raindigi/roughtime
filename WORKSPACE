workspace(name = "roughtime")

git_repository(
    name = "boringssl",
    commit = "9712e98fd90609a97e255eeaa5ae13c2db022620", # Sept 1st, 2016.
    remote = "https://boringssl.googlesource.com/boringssl",
)

git_repository(
    name = "protobuf",
    commit = "v3.0.0",
    remote = "https://github.com/google/protobuf",
)

new_http_archive(
    name = "gtest",
    url = "https://github.com/google/googletest/archive/release-1.7.0.tar.gz",
    sha256 = "f73a6546fdf9fce9ff93a5015e0333a8af3062a152a9ad6bcb772c96687016cc",
    build_file = "gtest.BUILD",
    strip_prefix = "googletest-release-1.7.0",
)
