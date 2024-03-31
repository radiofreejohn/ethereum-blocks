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
{
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

# Configuration

Make sure to edit:
- `prune`: set this to the number of blocks to keep behind the head block of the chain, I refer to this as N.
- `startBlock`: this can be the most recent block to make indexing fast, or the startBlock-N blocks to index the past N blocks.
- `network`: this should work on any EVM network, so change the network to match the network you want to index blocks for.
