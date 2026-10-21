# ADR-002: Use Koin framework for dependency injection

## Context

I considered:
1. **Hilt**: Google's official recommendation. *(Rejected: too heavy for first-time use)*
2. **Koin**: *(Chosen: aimed at Kotlin and lighter than Hilt)*

## Decision
I will use Koin for dependency injection.

## Consequences

### Positive:
- **Low cognitive load:** Setting up modules and injecting dependencies into ViewModels reads like plain, readable Kotlin code.
- **Easy testing & iteration:** Swapping dependencies or creating test configurations is straightforward without needing complex component setups.

### Negative / Trade-offs:
- **Runtime compilation**: Unlike Hilt or Dagger (which catch missing dependency errors at compile time), Koin resolves dependencies at runtime.
- **Not official recommendation**: While Koin has a robust community, it is not Google's officially recommended DI framework; official documentation and multiplatform integrations sometimes lag behind Google's tooling changes.
