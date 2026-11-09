# Gamma Toolkit architecture

## Repository model

Gamma Toolkit is a monorepo, not a single combined desktop application. The applications share a repository but remain independent software products.

```text
Gamma Toolkit
├── GGAPT                 -> standalone package and release
├── Gamma-Control-Center  -> standalone package and release
├── Gamma-Top             -> standalone package and release
└── shared                -> optional, carefully scoped common code
```

## Dependency boundaries

- An application may use system libraries available on its supported Debian targets.
- An application must not require another Gamma Toolkit application to be installed.
- Shared Python modules, if introduced, must have a clear API and must not create circular dependencies.
- Build dependencies and runtime dependencies must be declared separately by each application.

## Packaging and release boundaries

Each application owns its Debian packaging metadata, package name, version, changelog, tests, and release notes. CI should detect which application changed and build only the affected package where practical.

## Gamma Linux integration

Gamma Linux consumes the built application packages. The distribution repository remains responsible for selecting compatible package versions and integrating them into images; it should not need to duplicate each application's source tree.

## Source migration safety

Before migrating an existing application:

1. Inspect the original repository or archive.
2. Identify its current version, license, dependencies, and build process.
3. Preserve its history where practical.
4. Import without deleting or overwriting the original working copy.
5. Build, install, and test the imported version.
6. Update Gamma Linux integration only after verification.
