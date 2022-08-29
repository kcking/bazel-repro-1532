load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "rules_rust",
    sha256 = "6bfe75125e74155955d8a9854a8811365e6c0f3d33ed700bc17f39e32522c822",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_rust/releases/download/0.9.0/rules_rust-v0.9.0.tar.gz",
        "https://github.com/bazelbuild/rules_rust/releases/download/0.9.0/rules_rust-v0.9.0.tar.gz",
    ],
)

load("@rules_rust//rust:repositories.bzl", "rules_rust_dependencies", "rust_register_toolchains")

rules_rust_dependencies()

rust_register_toolchains(extra_target_triples = [
    "wasm32-unknown-unknown",
    "x86_64-unknown-linux-gnu",
    "aarch64-unknown-linux-gnu",
])

load("@rules_rust//crate_universe:repositories.bzl", "crate_universe_dependencies")

crate_universe_dependencies()

load("@rules_rust//crate_universe:defs.bzl", "crates_repository", "splicing_config")

crates_repository(
    name = "crate_index",
    cargo_lockfile = "//:Cargo.lock",
    lockfile = "//:cargo-bazel.lock.json",
    manifests = [
        "//:Cargo.toml",
    ],
    splicing_config = splicing_config(resolver_version = "2"),
)

load("@crate_index//:defs.bzl", "crate_repositories")

crate_repositories()

load("@rules_rust//wasm_bindgen:repositories.bzl", "rust_wasm_bindgen_repositories")

rust_wasm_bindgen_repositories()