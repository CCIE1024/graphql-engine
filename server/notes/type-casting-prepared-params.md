This note is in [Hasura.Backends.Postgres.SQL.Value](https://github.com/hasura/graphql-engine/blob/master/server/src-lib/Hasura/Backends/Postgres/SQL/Value.hs#L360).
It is referenced at:
  - line 848 of [Hasura.Backends.Postgres.SQL.Types](https://github.com/hasura/graphql-engine/blob/master/server/src-lib/Hasura/Backends/Postgres/SQL/Types.hs#L848)
  - line 371 of [Hasura.Backends.Postgres.SQL.Value](https://github.com/hasura/graphql-engine/blob/master/server/src-lib/Hasura/Backends/Postgres/SQL/Value.hs#L371)

# Type casting prepared params

Prepared values are passed to Postgres via text encoding. Explicit type cast for prepared params
is needed to distinguish the column types. For example, the parameter for citext column type is
generated as ($i)::citext where 'i' is parameter position (integer).

Also see https://github.com/hasura/graphql-engine/issues/2818

