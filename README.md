# Gamma Toolkit

**The official toolkit workspace for Gamma Linux.**

Gamma Toolkit is a monorepo for the standalone desktop utilities developed for the Gamma Linux ecosystem. Each application lives in its own directory and keeps its own source tree, documentation, tests, packaging metadata, version, and release process.

## Applications

| Application | Directory | Purpose | Status |
|---|---|---|---|
| **GGAPT** | [GGAPT/](GGAPT/) | Graphical front end for APT package management | Scaffold; source import pending |
| **Gamma Control Center** | [Gamma-Control-Center/](Gamma-Control-Center/) | Central place for Gamma desktop and system settings | Scaffold; source import pending |
| **Gamma Top** | [Gamma-Top/](Gamma-Top/) | Full graphical system monitor for Linux | Scaffold; implementation pending |

The status is intentionally explicit: creating this workspace does not mean the existing application source code has already been imported.

## Repository layout

```text
Gamma-Toolkit/
├── GGAPT/
├── Gamma-Control-Center/
├── Gamma-Top/
├── shared/
├── docs/
├── .github/
├── .editorconfig
├── .gitignore
├── CONTRIBUTING.md
├── LICENSE
└── README.md
```

## Project principles

- **Independent applications:** each tool must remain buildable and understandable on its own.
- **Independent releases:** applications have separate version numbers, changelogs, Debian packages, and release notes.
- **No unnecessary coupling:** one application must not depend on another just to run.
- **Shared code by design:** put code in `shared/` only when it is genuinely reusable, documented, and has a clear interface.
- **Debian-first packaging:** package each application separately for Gamma Linux and compatible Debian-based systems.
- **Lightweight native desktop:** prefer native Linux interfaces and the GTK stack where appropriate; avoid unnecessary web runtimes.
- **Preserve history and working copies:** source imports must be verified before any old copy or archive is retired.

## Build and releases

Each application will document its own dependencies and build instructions in its directory. CI workflows and release automation will be added after the real source trees and packaging metadata have been imported and verified. This avoids publishing workflows that pretend to build code that is not present yet.

Release tags use an application prefix so versions do not collide:

- `ggapt-vX.Y.Z`
- `control-center-vX.Y.Z`
- `gamma-top-vX.Y.Z`

## License

See [LICENSE](LICENSE). If an application has a different licensing history or needs its own license terms, preserve and review that application's license before importing its source. Do not assume that moving code into this repository changes its original license.
