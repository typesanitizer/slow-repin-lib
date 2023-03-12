load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "rules_rust",
    sha256 = "2466e5b2514772e84f9009010797b9cd4b51c1e6445bbd5b5e24848d90e6fb2e",
    urls = ["https://github.com/bazelbuild/rules_rust/releases/download/0.18.0/rules_rust-v0.18.0.tar.gz"],
)

# local_repository(
#     name = "rules_rust",
#     path = "../rules_rust",
# )

# rust toolchain setup
load("@rules_rust//rust:repositories.bzl", "rules_rust_dependencies", "rust_register_toolchains")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

rules_rust_dependencies()

rust_register_toolchains(
    edition = "2021",
    versions = ["1.68.0"],
)

load("@rules_rust//crate_universe:defs.bzl", "crates_repository")

crates_repository(
    name = "crate_index",
    cargo_config = "//:.cargo/config.toml",
    cargo_lockfile = "//:Cargo.lock",
    generator_sha256s = {
        "aarch64-apple-darwin": "98cede25600628fca842ec91d6faa151078ccf94961b20d3f46ea51cf545bb6b",
        "x86_64-unknown-linux-gnu": "1122ea0e832f250ff95a93ac52ed6519546bfe92befd54de45834860577e099b",
    },
    generator_urls = {
        "aarch64-apple-darwin": "https://github.com/bazelbuild/rules_rust/releases/download/0.18.0/cargo-bazel-aarch64-apple-darwin",
        "x86_64-unknown-linux-gnu": "https://github.com/bazelbuild/rules_rust/releases/download/0.18.0/cargo-bazel-x86_64-unknown-linux-gnu",
    },
    # To regenerate this file run: CARGO_BAZEL_REPIN=1 bazel sync --only=crate_index
    lockfile = "//:Cargo.Bazel.lock",
    manifests = ["//:Cargo.toml"],
)

load("@crate_index//:defs.bzl", "crate_repositories")

crate_repositories()
