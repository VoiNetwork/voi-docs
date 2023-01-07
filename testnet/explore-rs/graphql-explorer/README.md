# GraphQL Explorer

Voi testnet provides a GraphQL explorer for developers and advanced users

{% embed url="https://voitest-gql.algorpc.pro/graphiql" %}

```graphql
query OnlineStake {
  accounts(first: 100, condition: { isOnline: true }, orderBy: VOI_DESC) {
    edges {
      node {
        addr
        voi
        createdAt
        keytype
      }
    }
  }
  stake: accounts (first: 1, condition: {isOnline: true}) {
    online: aggregates {
      sum {
        voi
      }
    }
  }
}

```
