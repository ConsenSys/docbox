## Inspect Data

The `inspect` resource is available at this location:

Environment | Location
--- | ---
Production | `https://data.api.codefi.network/v0/inspect`

A _protocol_ contains fields relating to a protocol's configuration, like admin keys, governance, audits and oracles. The data is sources from [this Github repo](https://github.com/ConsenSys/inspect-data/)

The fields of a _protocol_ are defined as follows:

Field | Description
--- | ---
`machineName` | The name of the protocol without any formatting
`displayName` | The name of the protocol with formatting
`description` | A short description of the protocol
`audits` | A list of audits that the protocol has received with metadata
`adminTraits` | Information around admin keys such as address, timelock duration and whether the admin key uses a multisig

### List All Data

Lists the data of all platforms currently supported by Inspect

```endpoint
GET /v0/inspect
```

#### Example request

```curl
$ curl -X GET https://data.api.codefi.network/v0/inspect
```

#### Example response

```json
[
  {
    "machineName": "{platform}",
    "displayName": "{platform}",
    "description": "string",
    "audits": [{
      "date": "number",
      "auditor": "string",
      "engineeringWeeks": "number | null",
      "public": "boolean",
      "notes": "string",
      "link": "string",
    }],
    "adminTraits": [{
      "timelockEnabled": "boolean",
      "timelockHours": {
        "hours": "number"
      },
      "multisigEnabled": "boolean",
      "multisigOf": "string",
      "opsecClaimed": "boolean",
      "opsecClaimedNote": "string",
      "opsecVerified": "boolean",
      "opsecVerifiedNote": "string",
      "address": "string"
    }]
  },
  ...
]
```
