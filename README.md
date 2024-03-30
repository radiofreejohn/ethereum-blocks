# Ethereum Blocks Subgraph

A clone of an already great blocks subgraph, but this one prunes history so you only store the latest block, but can use time travel queries to get block information for N blocks in the past that are automatically pruned.

# Querying

## Latest Block
```graphql
{
  block(id:"latest_block"){
    id
    number
    timestamp
  }
}
```

## Historic Blocks as old as N blocks (defined by prune configuration in subgraph.yaml)

```graphql
{w
  blocks(block: { number: 404100 }){
    id
    number
    timestamp
  }
}
```

# Building

`yarn install && yarn codegen && yarn build`

Configurerd to deploy to [Goldsky](https://goldsky.com), but should work with other subgraph providers.
