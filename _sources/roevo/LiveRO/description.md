# roevo:LiveRO

A live Research Object that is mutable and can evolve before being snapshotted or archived.

- Purpose: represent an actively maintained RO.
- Typical transitions: `roevo:hasVersion`, `roevo:wasSnapshotOf` (from a snapshot), archival via `roevo:wasArchivedFrom`.
