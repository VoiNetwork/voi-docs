# Query examples

<details>

<summary>Online stake</summary>

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

</details>

<details>

<summary>MultipleAssetsInfo</summary>

```graphql
query MultipleAssetsInfo {
  assets (filter: {
    assetId : {
      in : [
        "31566704",
        "312769",
        "841126810"
      ]
    }
  }, first: 1000) {
    edges {
      node {
        freezeAddr
        unitName
        name
        url
        total
        decimals
        createdAt
      }
    }
  } 
  currentRound
}

```

</details>

<details>

<summary>Search for Humble v2 LP tokens</summary>

```graphql
query HumpleLT2 {
  assets(filter: { unitNameUni: { startsWith: "HMBL2" } }, last: 3) {
    nodes {
      assetId
      creatorAddr
      unitNameUni
      nameUni
      urlUni
      df
      total
      decimals
      deleted
      createdAt
      closedAt
    }
  }
}
```

</details>

<details>

<summary>Last 3 transactions for an account</summary>

```graphql
query AccountInfo {
  account(
    addrBin: "I4SUO77NG5FPUFCJW5YQVLQ5EGD3LZ3I3UG7WRAPGAESQEUQST4GBREBAA"
  ) {
    addr
    addrBin
    microvoi
    voi
    deleted
    createdAt
    closedAt
    keytype
    accountData
    txnParticipationsByAddrBin(last: 3) {
      nodes {
        transactionByRoundAndIntra {
          realtime
          typeenum
          type
          txidBin
          txid
          hasInners          
          isInner
          assetId
          appId
          assets
          apps
          assetsResolved(first: 256) {
            nodes {
              freezeAddr
              unitName
              name
              url
            }
          }
          txnInners(first:256) {
            nodes {
              intra
              typeenum
              amount
              addrSnd
              addrRcv
            }
          }
        }
      }
    }
  }

  currentRound
}


```

</details>
