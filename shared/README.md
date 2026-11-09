# Shared components

This directory is reserved for small, genuinely reusable components used by more than one Gamma Toolkit application.

Do not move code here only to avoid duplication. Before adding a shared component:

1. Identify at least two real consumers.
2. Define a narrow, documented API.
3. Avoid pulling one application's UI or runtime dependencies into another.
4. Add tests and document compatibility expectations.
5. Keep the component optional unless there is a strong architectural reason otherwise.

Application-specific code belongs in that application's own directory.
