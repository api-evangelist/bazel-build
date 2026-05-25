# Bazel

Bazel is a fast, scalable, multi-language and extensible build tool open-sourced by Google. It supports software
projects of any size across Java, C++, Go, Python, Rust, Swift, Kotlin, Scala, Android, iOS, and dozens of other
languages and platforms via community-maintained rulesets. Bazel uses a hermetic, sandboxed execution model with
content-addressable caching, fine-grained incremental builds, and the open Remote Execution API for distributed builds.

This repository is an [APIs.json](https://apisjson.org) catalog entry maintained by
[API Evangelist](https://apievangelist.com) covering the user-facing API surfaces of the Bazel ecosystem.

- **Homepage**: <https://bazel.build/>
- **Source**: <https://github.com/bazelbuild/bazel>
- **License**: Apache-2.0
- **Latest stable**: 9.1.0
- **Default registry**: <https://bcr.bazel.build/> (UI at <https://registry.bazel.build/>)

## APIs profiled

| API | Surface | Artifacts |
|---|---|---|
| Bazel Central Registry API | HTTP index registry — bcr.bazel.build | `openapi/bazel-central-registry-openapi.yml`, JSON Schemas |
| Bazel Command Line Interface | `bazel` CLI commands and flags | Documentation links |
| Bazel Starlark Build API | Rule, aspect, provider, module-extension primitives | Documentation links |
| Bazel Remote Execution API | gRPC REAPI for distributed builds and caching | `bazelbuild/remote-apis` proto |
| Bazel Build Event Protocol | Structured BEP/BES build-event stream | Build event proto |

## Repository layout

```
bazel-build/
├── apis.yml                              APIs.json catalog entry
├── README.md                             This file
├── openapi/
│   └── bazel-central-registry-openapi.yml
├── json-schema/
│   ├── bcr-bazel-registry-schema.json    /bazel_registry.json
│   ├── bcr-metadata-schema.json          /modules/{m}/metadata.json
│   └── bcr-source-schema.json            /modules/{m}/{v}/source.json
├── json-ld/
│   └── bazel-build-context.jsonld        Linked-data context
├── vocabulary/
│   └── bazel-build-vocabulary.yml        Bazel ecosystem terms
├── rules/
│   └── bazel-build-rules.yml             Spectral ruleset
├── capabilities/
│   └── bazel-central-registry.yaml       Naftiko capability composition
└── examples/
    ├── bcr-rules-python-metadata-example.json
    └── bcr-source-archive-example.json
```

## Bazel Central Registry as an API

The Bazel Central Registry exposes a small, stable HTTP surface that any Bazel-compatible registry can implement. It is
documented at <https://bazel.build/external/registry>:

| Path | Purpose |
|---|---|
| `/bazel_registry.json` | Registry-wide metadata: mirrors, module_base_path |
| `/modules/{module}/metadata.json` | Published versions and yanked-version notes |
| `/modules/{module}/{version}/MODULE.bazel` | Starlark manifest for that version |
| `/modules/{module}/{version}/source.json` | Archive URL + integrity, git ref, or local_path |
| `/modules/{module}/{version}/presubmit.yml` | BCR-specific CI presubmit configuration |

`openapi/bazel-central-registry-openapi.yml` describes that surface as an OpenAPI 3.0.3 contract.

## Key ecosystem repositories

- [bazelbuild/bazel](https://github.com/bazelbuild/bazel) — the build tool itself
- [bazelbuild/bazelisk](https://github.com/bazelbuild/bazelisk) — version launcher
- [bazelbuild/bazel-central-registry](https://github.com/bazelbuild/bazel-central-registry) — public module registry
- [bazelbuild/buildtools](https://github.com/bazelbuild/buildtools) — buildifier, buildozer, unused_deps
- [bazelbuild/bazel-gazelle](https://github.com/bazelbuild/bazel-gazelle) — BUILD file generator
- [bazelbuild/bazel-skylib](https://github.com/bazelbuild/bazel-skylib) — common Starlark library
- [bazelbuild/remote-apis](https://github.com/bazelbuild/remote-apis) — Remote Execution API (REAPI)
- Language rulesets: `rules_java`, `rules_cc`, `rules_python`, `rules_go`, `rules_rust`, `rules_swift`, `rules_apple`,
  `rules_kotlin`, `rules_scala`, `rules_nodejs`, `rules_docker`, `rules_oci`, `rules_proto`, `rules_pkg`, and many more.

## Maintainer

[Kin Lane](https://apievangelist.com) — API Evangelist · <info@apievangelist.com>
