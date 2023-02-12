load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

###
# Setup rules_js
# https://github.com/aspect-build/rules_js/releases
###
http_archive(
    name = "aspect_rules_js",
    sha256 = "3ad6684d744ebbc6592d404cc3aa81d0da634eccb3499f6fd198ae122fa28489",
    strip_prefix = "rules_js-1.19.0",
    url = "https://github.com/aspect-build/rules_js/releases/download/v1.19.0/rules_js-v1.19.0.tar.gz",
)

load("@aspect_rules_js//js:repositories.bzl", "rules_js_dependencies")

rules_js_dependencies()

load("@rules_nodejs//nodejs:repositories.bzl", "nodejs_register_toolchains")

nodejs_register_toolchains(
    name = "nodejs",
    node_version = "16.9.0",
)

load("@aspect_rules_js//npm:npm_import.bzl", "npm_translate_lock")

npm_translate_lock(
    name = "npm",
    pnpm_lock = "//:pnpm-lock.yaml",
    verify_node_modules_ignored = "//:.bazelignore",
)

load("@npm//:repositories.bzl", "npm_repositories")

npm_repositories()

###
# Setup rules_ts
# https://github.com/aspect-build/rules_ts/releases
###
http_archive(
    name = "aspect_rules_ts",
    sha256 = "db77d904284d21121ae63dbaaadfd8c75ff6d21ad229f92038b415c1ad5019cc",
    strip_prefix = "rules_ts-1.3.0",
    url = "https://github.com/aspect-build/rules_ts/releases/download/v1.3.0/rules_ts-v1.3.0.tar.gz",
)

load("@aspect_rules_ts//ts:repositories.bzl", "rules_ts_dependencies")

rules_ts_dependencies(ts_version_from = "//:package.json")

###
# Setup rules_swc
# https://github.com/aspect-build/rules_swc/releases
###
http_archive(
    name = "aspect_rules_swc",
    sha256 = "5d13b0123d91d4297f60d8da0ab5771615f6ad6829bdfe69e7dcda9e5c01bc54",
    strip_prefix = "rules_swc-1.0.0-rc0",
    url = "https://github.com/aspect-build/rules_swc/archive/refs/tags/v1.0.0-rc0.tar.gz",
)

load("@aspect_rules_swc//swc:dependencies.bzl", "rules_swc_dependencies")

rules_swc_dependencies()

load("@aspect_rules_swc//swc:repositories.bzl", "swc_register_toolchains", LATEST_SWC_VERSION = "LATEST_VERSION")

swc_register_toolchains(
    name = "swc",
    swc_version = LATEST_SWC_VERSION,
)

###
# Setup rules_pkg
# https://github.com/bazelbuild/rules_pkg/releases
###
http_archive(
    name = "rules_pkg",
    sha256 = "8c20f74bca25d2d442b327ae26768c02cf3c99e93fad0381f32be9aab1967675",
    url = "https://github.com/bazelbuild/rules_pkg/releases/download/0.8.1/rules_pkg-0.8.1.tar.gz",
)

load("@rules_pkg//:deps.bzl", "rules_pkg_dependencies")

rules_pkg_dependencies()

###
# Setup rules_docker
# https://github.com/bazelbuild/rules_docker/releases
###
http_archive(
    name = "io_bazel_rules_docker",
    sha256 = "b1e80761a8a8243d03ebca8845e9cc1ba6c82ce7c5179ce2b295cd36f7e394bf",
    urls = ["https://github.com/bazelbuild/rules_docker/releases/download/v0.25.0/rules_docker-v0.25.0.tar.gz"],
)

load("@io_bazel_rules_docker//repositories:repositories.bzl", rules_docker_repositories = "repositories")

rules_docker_repositories()

load("@io_bazel_rules_docker//repositories:deps.bzl", rules_docker_deps = "deps")

rules_docker_deps()

load("@io_bazel_rules_docker//container:container.bzl", "container_pull")

container_pull(
    name = "debian_amd64",
    architecture = "amd64",
    digest = "sha256:9a67b70d0ba1d7c7690f917eedd8d24974dd8fd493205368b1e555a90c954208",
    registry = "docker.io",
    repository = "debian",
)
