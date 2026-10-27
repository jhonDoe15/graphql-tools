# List-completion backport reference

This branch applies the list-result storage and lazy scalar-path changes proposed in
[PR #8617](https://github.com/ardatan/graphql-tools/pull/8617) and
[PR #8618](https://github.com/ardatan/graphql-tools/pull/8618) to the source of the published
`@graphql-tools/executor@1.5.7` tag.

It is a review/cherry-pick reference, not an upstream-maintained release branch or a published npm
replacement. Release-line coordination is discussed in
[issue #8616](https://github.com/ardatan/graphql-tools/issues/8616).

The patch preserves the existing dependency ranges, GraphQL peers and Node >=16 engine declaration.
It adds no new platform APIs. Local validation used Node 24.15.0 / GraphQL 16.13.2: 313 executor
tests pass, and the scoped Bob package build emits ESM, CJS and declarations. The Node 16 runtime
and other GraphQL peer versions have not been executed locally.

The completed-list optimization copies only executor-owned results; it does not read an input
array's length or alter its iterator. Custom scalar serialization, errors, promise paths and active
incremental streams keep their existing behavior.

Yoga 5 consumers using `^1.5.0` need a compatible maintainer-published patch to adopt this normally.
A forced executor 4.x override is not a substitute for that release.
