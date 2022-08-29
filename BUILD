load("@crate_index//:defs.bzl", "aliases", "all_crate_deps")
load("@rules_rust//rust:defs.bzl", "rust_binary")
load("@rules_rust//wasm_bindgen:wasm_bindgen.bzl", "rust_wasm_bindgen")


rust_binary(
    name = "bin",
    srcs = ["src/main.rs"],
    aliases = aliases(),
    edition = "2021",
    proc_macro_deps = all_crate_deps(
        proc_macro = True,
    ),
)

platform(
    name = "linux_arm64",
    constraint_values = [
        "@platforms//os:linux",
        "@platforms//cpu:arm64",
    ],
)

rust_wasm_bindgen(
    name = "wasm",
    wasm_file = ":bin",
)

filegroup(
    name="wasm-and-bin",
    srcs=[":wasm", ":bin"],
)