This note is in [Hasura.GraphQL.Execute.Subscription.Poll.Common](https://github.com/hasura/graphql-engine/blob/master/server/src-lib/Hasura/GraphQL/Execute/Subscription/Poll/Common.hs#L433).
It is referenced at:
  - line 366 of [Hasura.GraphQL.Execute.Subscription.Poll.Common](https://github.com/hasura/graphql-engine/blob/master/server/src-lib/Hasura/GraphQL/Execute/Subscription/Poll/Common.hs#L366)
  - line 443 of [Hasura.GraphQL.Execute.Subscription.Poll.Common](https://github.com/hasura/graphql-engine/blob/master/server/src-lib/Hasura/GraphQL/Execute/Subscription/Poll/Common.hs#L443)

# Minimal LiveQuery Poller Log

We only want to log the minimal information in the livequery-poller-log as it
could be expensive to log the details of every subscriber (all poller related
information can always be retrieved by dumping the current live queries state)
We capture a lot more details in PollDetails and BatchExecutionDetails than
that is logged currently as other implementations such as pro can use them if
they need to.

