This note is in [Hasura.Server.Logging](https://github.com/hasura/graphql-engine/blob/master/server/src-lib/Hasura/Server/Logging.hs#L267).
It is referenced at:
  - line 236 of [Hasura.Server.Logging](https://github.com/hasura/graphql-engine/blob/master/server/src-lib/Hasura/Server/Logging.hs#L236)
  - line 255 of [Hasura.Server.Logging](https://github.com/hasura/graphql-engine/blob/master/server/src-lib/Hasura/Server/Logging.hs#L255)
  - line 453 of [Hasura.Server.Logging](https://github.com/hasura/graphql-engine/blob/master/server/src-lib/Hasura/Server/Logging.hs#L453)

# Disable query printing for metadata queries

The 'olQuery' in the 'OperationLog' logs the actual query that is sent over HTTP.
This can lead to security issues, since the request sent in metadata queries may
include sensitive information such as DB URLS. Thus it is important that we hide
these sensitive information for the metadata URL.

As a temporary hotfix (ref: https://github.com/hasura/graphql-engine-mono/issues/3937),
If the URL path of HTTP requests is for a metadata operation and the
HASURA_GRAPHQL_ENABLE_METADATA_QUERY_LOGGING envirnoment variables is not set, then
we disable the 'query' field in HTTP logs.

