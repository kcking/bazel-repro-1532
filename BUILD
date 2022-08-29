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

rust_wasm_bindgen(
    name = "wasm",
    wasm_file = ":bin",
)

# in practice, this rule would be a web server compiled as native code that has
# a runtime wasm data dependency
filegroup(
    name="wasm-and-bin",
    srcs=[":wasm", ":bin"],
)