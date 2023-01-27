This note is in [Hasura.Backends.Postgres.Translate.Returning](https://github.com/hasura/graphql-engine/blob/master/server/src-lib/Hasura/Backends/Postgres/Translate/Returning.hs#L119).
It is referenced at:
  - line 38 of [Hasura.Backends.Postgres.Translate.Returning](https://github.com/hasura/graphql-engine/blob/master/server/src-lib/Hasura/Backends/Postgres/Translate/Returning.hs#L38)
  - line 143 of [Hasura.Backends.Postgres.Translate.Returning](https://github.com/hasura/graphql-engine/blob/master/server/src-lib/Hasura/Backends/Postgres/Translate/Returning.hs#L143)

# Mutation output expression

An example output expression for INSERT mutation:

WITH "mra__<table-name>" AS (
  INSERT INTO <table-name> (<insert-column>[..])
  VALUES
    (<insert-value-row>[..])
    ON CONFLICT ON CONSTRAINT "<table-constraint-name>" DO NOTHING RETURNING *,
    -- An extra column expression which performs the 'CHECK' validation
    (<CHECK Condition>) AS "check__constraint"
),
"aca__<table-name>" AS (
  -- Only extract columns from mutated rows. Columns sorted by ordinal position so that
  -- resulted rows can be casted to table type.
  SELECT (<table-column>[..])
  FROM
    "mra__<table-name>"
)
<SELECT statement to generate mutation response using 'aca__<table-name>' as FROM
 and bool_and("check__constraint") from "mra__<table-name>">

