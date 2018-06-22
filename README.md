# Protocol-Specification
/* Basic trust */
```

{
  "id": "KRBDm5sAKcmj84fj8qUsNAEROCRm7tBWU3utQss77AU=",
  "created": 1524569738,
  "issuer": {
    "type": "btc-pkh",
    "address": "jXPD0b2gvZfPXXQh/ylxSSTU9QQ=",
    "signature": "H9cdxdmEDtM+287JPV5aFtA1Axs5/74S4nf5ORwJVec2SwkNHoB6avTybq105yuwzhSjAYnA1icn2jgKHA22fvw="
  },
  "subject": {
    "address": "cnd9xXlQhg1mi4NB04kvVHv4JC4="
  },
  "type": "binarytrust.tc1",
  "claim": "{\"trust\":true}",
  "scope": {
    "type": "domain",
    "value": "www.reddit.com"
  },
  "cost": 100,
  "activate": 1231006505,
  "expire": 2231006505,
  "timestamp": [
    {
      "blockchain": "btc",
      "algorithm": "merkle.tc1-double256",
      "registered": 1524569739,
      "recipt": "DB5763238F5D93F35EBAA09A2A80922DEAB4A7EEEF642E98BE0663D7601418B3"
    }
  ]
}

// Merkle=Merkle algo, tc1=DTP version 1, double256=sha256(sha256))
// Transaction time used for the timestamp
// Merkletree path or description text, used for recreating the merkle root value.

/*
A package of Trust
Its a way for sharing trust between servers.

{
  "algorithm": "merkle.tc1-double256", // Merkle=Merkle algo, tc1=DTP version 1, double256=sha256(sha256))
  "id": "", // Merkle root of the trust ids.
  "trusts": [
    {
      "algorithm": "double256", // Algo to be used for calculating the id of the trust. Default is double sha256
      "id": "i/Pd9j9fDh0GGt5pPhAQfq2RsI8mcYmM/vfNhm1Qql0=", // A hash of the binary combined value of the trust
      "issuer": {
        "type": "btc-pkh",
        "address": "F2u5DwkfJUjVDy7gCDp68hbQUDM=", // Base64 encoding of a 20 byte address
        "signature": "H/hqGOZwZNz2/rz0udzyx4eHLzTMvx67ASmp0whBbjq0JAoJokrRnDAWsHNgBQtlYifoH3SG5pjbgS/9+H4Ukuc="
      },
      "subjects": [
        {
          "type": "btc-pkh", // Specifies the type of the id. Helps on filtering on Trust resolvement.
          "address": "1ERgQJdwncLvXv16mQaKu...", // id of the subject, data and format of the address can be anything.
          "signature": "", // 
        }
      ],
      "type": "binarytrust.tc1", // The type of the trust
      "claim": "{\"trust\":true}", // The claim attached to this trust

      // Scope is used to filter on trust resolvement. It can be any text
      "scope": {
          "type" : "", // Specifies the format of the scope value
          "value" : "local", // The scope could also be specefic to country, area, products, articles or social medias etc. Global is default.
      },

      "cost": 100,
      // This is a cost when resolving the trust. A more nodes are followed with low values.
      // The cost property can only have a value below 100 if the subject signature is provided. This helps e.g. search companies.
      // The cost value cannot be below 1 (avoid infinite loop).

      "activate": 1231006505, // When will the trust be active. unixepoch
      "expire": 2231006505, // When will the trust deactivate. unixepoch
      // The timestamp is used when the trust is repackaged into an other package
      "timestamp": [
          {
          "blockchain": "btc", // The blockchain used for the timestamp
          "algorithm": "merkle.tc1-double256", // Merkle=Merkle algo, tc1=DTP version 1, double256=sha256(sha256))
          "registered": 1231006505, // Transaction time used for the timestamp
          "recipt": "", // Merkletree path or description text, used for recreating the merkle root value.
          "service": "" // Optional, the url or name of the service provided the timestamp
          }
        ]
    }
  ],
  // The server that creates the package
  "server": {
    "type": "btc-pkh",
    "address": "",
    "signature": ""
  },
  // Timestamps of the package
  "timestamps": [ // Array of timestamps, then fast and slow timestamps are possible
    {
      "blockchain": "btc", // The blockchain used for the timestamp
      "algorithm": "merkle.tc1-double256", // Merkle=Merkle algo, tc1=DTP version 1, double256=sha256(sha256))
      "registered": 1231006505, // Transaction time used for the timestamp
      "recipt": "", // Merkletree path or description text, used for recreating the merkle root value.
      "service": "" // Optional, the url or name of the service provided the timestamp
    }
  ]
}
*/

```
