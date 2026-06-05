# Bazel (bazel-build)

Bazel is a fast, scalable, multi-language and extensible build tool open-sourced by Google. It supports software projects of any size across Java, C++, Go, Python, Rust, Swift, Kotlin, Scala, Android, iOS, and many other languages and platforms. Bazel uses a hermetic, sandboxed execution model with content-addressable caching, parallel builds, and remote execution. The project ships the `bazel` CLI, the Starlark extension language for build rules, the MODULE.bazel external-dependency system (Bzlmod), and the Bazel Central Registry — a public HTTP index registry that hosts community-maintained Bazel modules.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/bazel-build/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/bazel-build/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consumer
- **Access:** 3rd-Party

## Tags

- Build Systems
- Build Tool
- Bzlmod
- CI/CD
- Developer Tools
- Hermetic Builds
- Monorepo
- Open Source
- Remote Execution
- Starlark

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## APIs

### Bazel Central Registry API

The Bazel Central Registry (BCR) is the default index registry consulted by Bzlmod, Bazel's external dependency management system. The BCR exposes a stable HTTP layout at https://bcr.bazel.build/ that serves a registry-wide bazel_registry.json plus per-module metadata.json, MODULE.bazel manifests, and source.json fetch instructions. Since Bazel 8 Bzlmod is on by default, making the BCR the registry every Bazel install resolves against unless --registry is overridden.

- **Human URL:** [https://registry.bazel.build/](https://registry.bazel.build/)
- **Base URL:** `https://bcr.bazel.build`

#### Tags

- Bzlmod
- Index Registry
- Modules
- Package Registry

#### Properties

- [Documentation](https://bazel.build/external/registry)
- [Documentation](https://bazel.build/external/module)
- [Portal](https://registry.bazel.build/)
- [OpenAPI](openapi/bazel-central-registry-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/bazel-central-registry.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/bazel-central-registry.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/bcr-bazel-registry-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/bcr-metadata-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/bcr-source-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [GitHub Repository](https://github.com/bazelbuild/bazel-central-registry)

### Bazel Command Line Interface

The `bazel` command line tool is the primary user-facing surface of Bazel. It exposes commands such as `build`, `test`, `run`, `query`, `cquery`, `aquery`, `mod`, `fetch`, `info`, `coverage`, and `clean`, plus the BEP/BES streaming protocols for build event publishing. Bazelisk is the recommended launcher that pins the Bazel version per project via .bazelversion.

- **Human URL:** [https://bazel.build/reference/command-line-reference](https://bazel.build/reference/command-line-reference)

#### Tags

- CLI
- Commands
- Tooling

#### Properties

- [Documentation](https://bazel.build/reference/command-line-reference)
- [Documentation](https://bazel.build/run/build)
- [Documentation](https://bazel.build/query/language)
- [Tool](https://github.com/bazelbuild/bazel)
- [Tool](https://github.com/bazelbuild/bazelisk)
- [Postman Collection](collections/bazel-central-registry.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/bazel-central-registry.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Bazel Starlark Build API

Bazel's build rules, macros, and module extensions are written in Starlark — a deterministic Python dialect. The Starlark Build API exposes the rule(), repository_rule(), module_extension(), aspect(), and provider() primitives used to declare build targets, generate actions, and integrate new languages. BUILD, BUILD.bazel, .bzl, MODULE.bazel, and WORKSPACE files are all evaluated by this API.

- **Human URL:** [https://bazel.build/rules](https://bazel.build/rules)

#### Tags

- BUILD
- DSL
- Extension
- Rules
- Starlark

#### Properties

- [Documentation](https://bazel.build/rules)
- [Documentation](https://bazel.build/rules/language)
- [Documentation](https://bazel.build/extending/concepts)
- [API Reference](https://bazel.build/rules/lib/starlark-overview)
- [Postman Collection](collections/bazel-central-registry.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/bazel-central-registry.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Bazel Remote Execution API

Bazel speaks the open Remote Execution API (REAPI), a gRPC protocol for content-addressable storage and distributed action execution. REAPI lets Bazel offload compile, test, and link actions to a remote build farm and share a Content-Addressable Store (CAS) and Action Cache across users and CI runners. Bazel implements the client side; servers such as BuildBuddy, EngFlow, Buildbarn, Buildfarm, and Google RBE implement the server side.

- **Human URL:** [https://github.com/bazelbuild/remote-apis](https://github.com/bazelbuild/remote-apis)

#### Tags

- CAS
- Caching
- Distributed Builds
- gRPC
- Remote Execution

#### Properties

- [Documentation](https://bazel.build/remote/rbe)
- [Documentation](https://bazel.build/remote/caching)
- [GitHub Repository](https://github.com/bazelbuild/remote-apis)
- [Protocol Buffer](https://github.com/bazelbuild/remote-apis/blob/main/build/bazel/remote/execution/v2/remote_execution.proto)
- [Postman Collection](collections/bazel-central-registry.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/bazel-central-registry.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Bazel Build Event Protocol

The Build Event Protocol (BEP) is Bazel's structured stream of build events — target configured, progress, test results, action executed, build finished — emitted during every invocation. BEP can be written to a local file (--build_event_json_file / --build_event_binary_file) or streamed via gRPC to a Build Event Service (BES) backend for build observability, flake analysis, and CI dashboards.

- **Human URL:** [https://bazel.build/remote/bep](https://bazel.build/remote/bep)

#### Tags

- BEP
- BES
- Build Events
- Observability
- Streaming

#### Properties

- [Documentation](https://bazel.build/remote/bep)
- [Documentation](https://bazel.build/remote/bep-examples)
- [Protocol Buffer](https://github.com/bazelbuild/bazel/blob/master/src/main/java/com/google/devtools/build/lib/buildeventstream/proto/build_event_stream.proto)
- [Postman Collection](collections/bazel-central-registry.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/bazel-central-registry.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Portal](https://bazel.build/)
- [Documentation](https://bazel.build/docs)
- [Getting Started](https://bazel.build/start)
- [API Reference](https://bazel.build/reference)
- [Blog](https://blog.bazel.build/)
- [GitHub Organization](https://github.com/bazelbuild)
- [GitHub Repository](https://github.com/bazelbuild/bazel)
- [GitHub Repository](https://github.com/bazelbuild/bazel-central-registry)
- [GitHub Repository](https://github.com/bazelbuild/bazelisk)
- [GitHub Repository](https://github.com/bazelbuild/buildtools)
- [GitHub Repository](https://github.com/bazelbuild/bazel-gazelle)
- [GitHub Repository](https://github.com/bazelbuild/bazel-skylib)
- [GitHub Repository](https://github.com/bazelbuild/remote-apis)
- [Changelog](https://github.com/bazelbuild/bazel/releases)
- [Issues](https://github.com/bazelbuild/bazel/issues)
- [Roadmap](https://bazel.build/about/roadmap)
- [Governance](https://bazel.build/contribute/contribution-policy)
- [Terms of Service](https://github.com/bazelbuild/bazel/blob/master/LICENSE)
- [Security](https://bazel.build/about/security)
- [Forum](https://slack.bazel.build/)
- [Stack Overflow](https://stackoverflow.com/questions/tagged/bazel)
- [Tool](https://github.com/bazelbuild/bazelisk)
- [Tool](https://github.com/bazelbuild/buildtools)
- [Tool](https://github.com/bazelbuild/bazel-gazelle)
- [SDK](https://github.com/bazelbuild/rules_java)
- [SDK](https://github.com/bazelbuild/rules_cc)
- [SDK](https://github.com/bazelbuild/rules_python)
- [SDK](https://github.com/bazelbuild/rules_go)
- [SDK](https://github.com/bazelbuild/rules_rust)
- [SDK](https://github.com/bazelbuild/rules_swift)
- [SDK](https://github.com/bazelbuild/rules_apple)
- [SDK](https://github.com/bazelbuild/rules_kotlin)
- [SDK](https://github.com/bazelbuild/rules_scala)
- [SDK](https://github.com/bazelbuild/rules_nodejs)
- [SDK](https://github.com/bazelbuild/rules_docker)
- [SDK](https://github.com/bazelbuild/rules_oci)
- [SDK](https://github.com/bazelbuild/rules_proto)
- [SDK](https://github.com/bazelbuild/rules_pkg)
- [SDK](https://github.com/bazelbuild/bazel-skylib)
- [Plugins](https://github.com/bazelbuild/intellij)
- [Plugins](https://github.com/bazelbuild/vscode-bazel)
- [Code Examples](https://github.com/bazelbuild/examples)
- [Vocabulary](vocabulary/bazel-build-vocabulary.yml)
- [JSON-LD](json-ld/bazel-build-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)
- [Spectral Rules](rules/bazel-build-rules.yml)
- [License](https://github.com/bazelbuild/bazel/blob/master/LICENSE)
- [Features](undefined)

## Maintainers

**FN:** Kin Lane
**Email:** info@apievangelist.com
**URL:** https://apievangelist.com
