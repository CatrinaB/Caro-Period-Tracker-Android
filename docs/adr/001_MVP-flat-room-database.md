# ADR-001: Use a flat database structure in Android Room and hard-coded symptoms for MVP

## Context
The aim of the MVP is to allow users to select one or more symptoms and log them into the database. To keep things simple, I will use a flat database until I get a good idea on how I want the 
data to be stores(SQL/NoSQL, relationships, tables, etc.)

Using Room because it's well integrated into Android and Compose.

Other options:
1. **Full relational schema**: *(Rejected: too much overhead, too much work to migrate to a different schema)*
2. **NoSQL local DB**: *(Rejected: Room (SQLite) is the standard native Android tool with better official support)*
3. **Flat table with comma-separated strings**: Storing all metrics in a single table with an optional comma-separated string for multi-select options. *(Chosen)*

## Decision
I will use a **flat table structure** (`symptom_entry_history`) in Android Room. 
- All entry types will share a single entity schema.
- Fixed symptom choices will be represented via a Kotlin `enum class` and serialized into a comma-separated string (`selectedSymptoms`) within the flat entity.

## Consequences
- **Positive:** 
  - Zero database migration overhead when adding new metric types or symptom options.
  - Extremely fast implementation time.
  - Simple DAO queries using SQLite text matching.
- **Negative / Trade-offs:** 
  - Cannot add custom symptoms. *(Acceptable for MVP, will be a feature in a future version)*
  - Schema not well-defined. *(MVP goal is code implementation and basic documentation, no need for complex design choices at this point)*
