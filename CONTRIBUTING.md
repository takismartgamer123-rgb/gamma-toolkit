# Contributing to Gamma Toolkit

Thanks for contributing to the Gamma Linux toolkit.

## Choose the right application directory

Keep application-specific code inside its own directory:

- `GGAPT/`
- `Gamma-Control-Center/`
- `Gamma-Top/`

Do not place application code at the repository root.

## Keep applications independent

Each application should maintain its own:

- README and user-facing documentation
- source code and resources
- tests
- dependency declarations
- Debian packaging files
- version and changelog
- build and release instructions

Avoid runtime dependencies between applications. A shared module belongs in `shared/` only when more than one application needs it and its API can be kept stable and documented.

## Changes

1. Explain which application a change affects.
2. Add or update tests when behavior changes.
3. Update that application's documentation and changelog.
4. Keep commits focused; do not mix unrelated application changes.
5. Never remove an existing source copy or archive as part of an import until the new copy has been verified.

## Packaging

Build and test each Debian package independently. Do not add a CI workflow that reports success without building and validating the actual application package.

## Licensing

Preserve copyright notices and the original license of imported code. Ask for a licensing review before combining code with different license terms.
