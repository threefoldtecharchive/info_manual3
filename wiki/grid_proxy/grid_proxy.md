> IMPORTANT NOTICE (05/03/2023): 
The information of this page is outdated. ThreeFold team is in the process of migrating this this manual to its new home on manual.grid.tf. Please go to [manual.grid.tf](https://manual.grid.tf/) to read the latest documentation of ThreeFold.

<h1 id="grid-proxy-server-api">Grid Proxy Server API v1.0</h1>

What is Grid Proxy Server API?

The Grid Proxy Server API is a set of web services that allow developers to access the data about TF grid. The API design is flexible and easy to use, allowing developers to integrate the data into their applications. API provides access to data items such nodes, farms, and contracts. The API is available in REST architecture with JSON responses.

How do I Use Grid Proxy Server API?

For trying the API you can use the swagger to make live calls to the API server, or use one of the API client libraries to make calls to the API server.
in the doc, You will also find some sample codes written in Bash, Python and javascript, which you can use to test the API alongside the API specs and documentation.

Base URLs:

* <a href="https://gridproxy.dev.grid.tf/">https://gridproxy.dev.grid.tf/</a> - Dev Network
* <a href="https://gridproxy.test.grid.tf">https://gridproxy.test.grid.tf</a> - Test Network
* <a href="https://gridproxy.qa.grid.tf">https://gridproxy.qa.grid.tf</a> - QA Network
* <a href="https://gridproxy.grid.tf">https://gridproxy.grid.tf</a> - Main Network

Try it for yourself

Swagger:

swagger is an interactive tool to make live calls to the API server

* <a href="https://gridproxy.dev.grid.tf/swagger/index.html">https://gridproxy.dev.grid.tf/swagger/index.html</a> - Dev Network
* <a href="https://gridproxy.test.grid.tf/swagger/index.html">https://gridproxy.test.grid.tf/swagger/index.html</a> - Test Network
* <a href="https://gridproxy.qa.grid.tf/swagger/index.html">https://gridproxy.qa.grid.tf/swagger/index.html</a> - QA Network
* <a href="https://gridproxy.main.grid.tf/swagger/index.html">https://gridproxy.main.grid.tf/swagger/index.html</a> - Main Network

Installation and Production setup:

* <a href="https://github.com/threefoldtech/tfgridclient_proxy">Github Documentation</a>

Using Client Libraries:

While you can use Grid Proxy Server APIs directly by making raw requests to the server, client libraries provide simplifications that significantly reduce the amount of code you need to write.

* V lang: <a href="https://github.com/threefoldtech/vgrid/tree/development/gridproxy">VGrid Documentation</a> 

License: <a href="http://www.apache.org/licenses/LICENSE-2.0.html">Apache 2.0</a>

> Scroll down for code samples, example requests and responses.

<h1 id="grid-proxy-server-api-gridproxy">GridProxy</h1>

## get__contracts

> Code samples

```shell
# You can also use wget
curl -X GET /contracts \
  -H 'Accept: application/json'

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('/contracts', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/contracts',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /contracts`

*Show contracts on the grid*

Get all contracts on the grid, It has pagination

<h3 id="get__contracts-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|page|query|integer|false|Page number|
|size|query|integer|false|Max result per page|
|ret_count|query|string|false|Set farms' count on headers based on filter|
|contract_id_id|query|integer|false|contract id|
|twin_id|query|integer|false|twin id|
|node_id|query|integer|false|node id which contract is deployed on in case of ('rent' or 'node' contracts)|
|name|query|string|false|contract name in case of 'name' contracts|
|type|query|string|false|contract type 'node', 'name', or 'rent'|
|state|query|string|false|contract state 'Created', or 'Deleted'|
|deployment_data|query|string|false|contract deployment data in case of 'node' contracts|
|deployment_hash|query|string|false|contract deployment hash in case of 'node' contracts|
|number_of_public_ips|query|integer|false|Min number of public ips in the 'node' contract|

> Example responses

> 200 Response

```json
[
  {
    "billing": [
      {
        "amountBilled": 0,
        "discountReceived": "string",
        "timestamp": 0
      }
    ],
    "contractId": 0,
    "created_at": 0,
    "details": null,
    "state": "string",
    "twinId": 0,
    "type": "string"
  }
]
```

<h3 id="get__contracts-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|

<h3 id="get__contracts-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[explorer.contract](#schemaexplorer.contract)]|false|none|none|
|» billing|[[db.ContractBilling](#schemadb.contractbilling)]|false|none|none|
|»» amountBilled|integer|false|none|none|
|»» discountReceived|string|false|none|none|
|»» timestamp|integer|false|none|none|
|» contractId|integer|false|none|none|
|» created_at|integer|false|none|none|
|» details|any|false|none|none|
|» state|string|false|none|none|
|» twinId|integer|false|none|none|
|» type|string|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## get__farms

> Code samples

```shell
# You can also use wget
curl -X GET /farms \
  -H 'Accept: application/json'

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('/farms', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/farms',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /farms`

*Show farms on the grid*

Get all farms on the grid, It has pagination

<h3 id="get__farms-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|page|query|integer|false|Page number|
|size|query|integer|false|Max result per page|
|ret_count|query|string|false|Set farms' count on headers based on filter|
|free_ips|query|integer|false|Min number of free ips in the farm|
|total_ips|query|integer|false|Min number of total ips in the farm|
|pricing_policy_id|query|integer|false|Pricing policy id|
|version|query|integer|false|farm version|
|farm_id|query|integer|false|farm id|
|twin_id|query|integer|false|twin id associated with the farm|
|name|query|string|false|farm name|
|name_contains|query|string|false|farm name contains|
|certification_type|query|string|false|certificate type DIY or Certified|
|dedicated|query|boolean|false|farm is dedicated|
|stellar_address|query|string|false|farm stellar_address|

> Example responses

> 200 Response

```json
[
  {
    "certificationType": "string",
    "dedicated": true,
    "farmId": 0,
    "name": "string",
    "pricingPolicyId": 0,
    "publicIps": [
      {
        "contractId": 0,
        "farmId": "string",
        "gateway": "string",
        "id": "string",
        "ip": "string"
      }
    ],
    "stellarAddress": "string",
    "twinId": 0
  }
]
```

<h3 id="get__farms-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|

<h3 id="get__farms-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[explorer.farm](#schemaexplorer.farm)]|false|none|none|
|» certificationType|string|false|none|none|
|» dedicated|boolean|false|none|none|
|» farmId|integer|false|none|none|
|» name|string|false|none|none|
|» pricingPolicyId|integer|false|none|none|
|» publicIps|[[db.PublicIP](#schemadb.publicip)]|false|none|none|
|»» contractId|integer|false|none|none|
|»» farmId|string|false|none|none|
|»» gateway|string|false|none|none|
|»» id|string|false|none|none|
|»» ip|string|false|none|none|
|» stellarAddress|string|false|none|none|
|» twinId|integer|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## get__gateways

> Code samples

```shell
# You can also use wget
curl -X GET /gateways \
  -H 'Accept: application/json'

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('/gateways', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/gateways',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /gateways`

*Show nodes on the grid*

Get all nodes on the grid, It has pagination

<h3 id="get__gateways-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|page|query|integer|false|Page number|
|size|query|integer|false|Max result per page|
|ret_count|query|string|false|Set nodes' count on headers based on filter|
|free_mru|query|integer|false|Min free reservable mru in bytes|
|free_hru|query|integer|false|Min free reservable hru in bytes|
|free_sru|query|integer|false|Min free reservable sru in bytes|
|free_ips|query|integer|false|Min number of free ips in the farm of the node|
|status|query|string|false|Node status filter, up/down.|
|city|query|string|false|Node city filter|
|country|query|string|false|Node country filter|
|farm_name|query|string|false|Get nodes for specific farm|
|ipv4|query|string|false|Set to true to filter nodes with ipv4|
|ipv6|query|string|false|Set to true to filter nodes with ipv6|
|domain|query|string|false|Set to true to filter nodes with domain|
|dedicated|query|boolean|false|Set to true to get the dedicated nodes only|
|rentable|query|boolean|false|Set to true to filter the available nodes for renting|
|rented_by|query|integer|false|rented by twin id|
|available_for|query|integer|false|available for twin id|
|farm_ids|query|string|false|List of farms separated by comma to fetch nodes from (e.g. '1,2,3')|

> Example responses

> 200 Response

```json
[
  {
    "certificationType": "string",
    "city": "string",
    "country": "string",
    "created": 0,
    "dedicated": true,
    "farmId": 0,
    "farmingPolicyId": 0,
    "gridVersion": 0,
    "id": "string",
    "location": {
      "city": "string",
      "country": "string"
    },
    "nodeId": 0,
    "publicConfig": {
      "domain": "string",
      "gw4": "string",
      "gw6": "string",
      "ipv4": "string",
      "ipv6": "string"
    },
    "rentContractId": 0,
    "rentedByTwinId": 0,
    "status": "string",
    "total_resources": {
      "cru": 0,
      "hru": 0,
      "mru": 0,
      "sru": 0
    },
    "twinId": 0,
    "updatedAt": 0,
    "uptime": 0,
    "used_resources": {
      "cru": 0,
      "hru": 0,
      "mru": 0,
      "sru": 0
    }
  }
]
```

<h3 id="get__gateways-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|

<h3 id="get__gateways-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[explorer.node](#schemaexplorer.node)]|false|none|none|
|» certificationType|string|false|none|none|
|» city|string|false|none|none|
|» country|string|false|none|none|
|» created|integer|false|none|none|
|» dedicated|boolean|false|none|none|
|» farmId|integer|false|none|none|
|» farmingPolicyId|integer|false|none|none|
|» gridVersion|integer|false|none|none|
|» id|string|false|none|none|
|» location|[explorer.location](#schemaexplorer.location)|false|none|none|
|»» city|string|false|none|none|
|»» country|string|false|none|none|
|» nodeId|integer|false|none|none|
|» publicConfig|[db.PublicConfig](#schemadb.publicconfig)|false|none|none|
|»» domain|string|false|none|none|
|»» gw4|string|false|none|none|
|»» gw6|string|false|none|none|
|»» ipv4|string|false|none|none|
|»» ipv6|string|false|none|none|
|» rentContractId|integer|false|none|none|
|» rentedByTwinId|integer|false|none|none|
|» status|string|false|none|added node status field for up or down|
|» total_resources|[db.Capacity](#schemadb.capacity)|false|none|none|
|»» cru|integer|false|none|none|
|»» hru|integer|false|none|none|
|»» mru|integer|false|none|none|
|»» sru|integer|false|none|none|
|» twinId|integer|false|none|none|
|» updatedAt|integer|false|none|none|
|» uptime|integer|false|none|none|
|» used_resources|[db.Capacity](#schemadb.capacity)|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## get__gateways_{node_id}

> Code samples

```shell
# You can also use wget
curl -X GET /gateways/{node_id} \
  -H 'Accept: application/json'

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('/gateways/{node_id}', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/gateways/{node_id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /gateways/{node_id}`

*Show the details for specific node*

Get all details for specific node hardware, capacity, DMI, hypervisor

<h3 id="get__gateways_{node_id}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|node_id|path|integer|true|Node ID|

> Example responses

> 200 Response

```json
{
  "certificationType": "string",
  "city": "string",
  "country": "string",
  "created": 0,
  "dedicated": true,
  "farmId": 0,
  "farmingPolicyId": 0,
  "gridVersion": 0,
  "id": "string",
  "location": {
    "city": "string",
    "country": "string"
  },
  "nodeId": 0,
  "publicConfig": {
    "domain": "string",
    "gw4": "string",
    "gw6": "string",
    "ipv4": "string",
    "ipv6": "string"
  },
  "rentContractId": 0,
  "rentedByTwinId": 0,
  "status": "string",
  "total_resources": {
    "cru": 0,
    "hru": 0,
    "mru": 0,
    "sru": 0
  },
  "twinId": 0,
  "updatedAt": 0,
  "uptime": 0,
  "used_resources": {
    "cru": 0,
    "hru": 0,
    "mru": 0,
    "sru": 0
  }
}
```

<h3 id="get__gateways_{node_id}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[explorer.node](#schemaexplorer.node)|

<aside class="success">
This operation does not require authentication
</aside>

## get__nodes

> Code samples

```shell
# You can also use wget
curl -X GET /nodes \
  -H 'Accept: application/json'

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('/nodes', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/nodes',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /nodes`

*Show nodes on the grid*

Get all nodes on the grid, It has pagination

<h3 id="get__nodes-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|page|query|integer|false|Page number|
|size|query|integer|false|Max result per page|
|ret_count|query|string|false|Set nodes' count on headers based on filter|
|free_mru|query|integer|false|Min free reservable mru in bytes|
|free_hru|query|integer|false|Min free reservable hru in bytes|
|free_sru|query|integer|false|Min free reservable sru in bytes|
|free_ips|query|integer|false|Min number of free ips in the farm of the node|
|status|query|string|false|Node status filter, up/down.|
|city|query|string|false|Node city filter|
|country|query|string|false|Node country filter|
|farm_name|query|string|false|Get nodes for specific farm|
|ipv4|query|string|false|Set to true to filter nodes with ipv4|
|ipv6|query|string|false|Set to true to filter nodes with ipv6|
|domain|query|string|false|Set to true to filter nodes with domain|
|dedicated|query|boolean|false|Set to true to get the dedicated nodes only|
|rentable|query|boolean|false|Set to true to filter the available nodes for renting|
|rented_by|query|integer|false|rented by twin id|
|available_for|query|integer|false|available for twin id|
|farm_ids|query|string|false|List of farms separated by comma to fetch nodes from (e.g. '1,2,3')|

> Example responses

> 200 Response

```json
[
  {
    "certificationType": "string",
    "city": "string",
    "country": "string",
    "created": 0,
    "dedicated": true,
    "farmId": 0,
    "farmingPolicyId": 0,
    "gridVersion": 0,
    "id": "string",
    "location": {
      "city": "string",
      "country": "string"
    },
    "nodeId": 0,
    "publicConfig": {
      "domain": "string",
      "gw4": "string",
      "gw6": "string",
      "ipv4": "string",
      "ipv6": "string"
    },
    "rentContractId": 0,
    "rentedByTwinId": 0,
    "status": "string",
    "total_resources": {
      "cru": 0,
      "hru": 0,
      "mru": 0,
      "sru": 0
    },
    "twinId": 0,
    "updatedAt": 0,
    "uptime": 0,
    "used_resources": {
      "cru": 0,
      "hru": 0,
      "mru": 0,
      "sru": 0
    }
  }
]
```

<h3 id="get__nodes-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|

<h3 id="get__nodes-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[explorer.node](#schemaexplorer.node)]|false|none|none|
|» certificationType|string|false|none|none|
|» city|string|false|none|none|
|» country|string|false|none|none|
|» created|integer|false|none|none|
|» dedicated|boolean|false|none|none|
|» farmId|integer|false|none|none|
|» farmingPolicyId|integer|false|none|none|
|» gridVersion|integer|false|none|none|
|» id|string|false|none|none|
|» location|[explorer.location](#schemaexplorer.location)|false|none|none|
|»» city|string|false|none|none|
|»» country|string|false|none|none|
|» nodeId|integer|false|none|none|
|» publicConfig|[db.PublicConfig](#schemadb.publicconfig)|false|none|none|
|»» domain|string|false|none|none|
|»» gw4|string|false|none|none|
|»» gw6|string|false|none|none|
|»» ipv4|string|false|none|none|
|»» ipv6|string|false|none|none|
|» rentContractId|integer|false|none|none|
|» rentedByTwinId|integer|false|none|none|
|» status|string|false|none|added node status field for up or down|
|» total_resources|[db.Capacity](#schemadb.capacity)|false|none|none|
|»» cru|integer|false|none|none|
|»» hru|integer|false|none|none|
|»» mru|integer|false|none|none|
|»» sru|integer|false|none|none|
|» twinId|integer|false|none|none|
|» updatedAt|integer|false|none|none|
|» uptime|integer|false|none|none|
|» used_resources|[db.Capacity](#schemadb.capacity)|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## get__nodes_{node_id}

> Code samples

```shell
# You can also use wget
curl -X GET /nodes/{node_id} \
  -H 'Accept: application/json'

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('/nodes/{node_id}', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/nodes/{node_id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /nodes/{node_id}`

*Show the details for specific node*

Get all details for specific node hardware, capacity, DMI, hypervisor

<h3 id="get__nodes_{node_id}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|node_id|path|integer|true|Node ID|

> Example responses

> 200 Response

```json
{
  "certificationType": "string",
  "city": "string",
  "country": "string",
  "created": 0,
  "dedicated": true,
  "farmId": 0,
  "farmingPolicyId": 0,
  "gridVersion": 0,
  "id": "string",
  "location": {
    "city": "string",
    "country": "string"
  },
  "nodeId": 0,
  "publicConfig": {
    "domain": "string",
    "gw4": "string",
    "gw6": "string",
    "ipv4": "string",
    "ipv6": "string"
  },
  "rentContractId": 0,
  "rentedByTwinId": 0,
  "status": "string",
  "total_resources": {
    "cru": 0,
    "hru": 0,
    "mru": 0,
    "sru": 0
  },
  "twinId": 0,
  "updatedAt": 0,
  "uptime": 0,
  "used_resources": {
    "cru": 0,
    "hru": 0,
    "mru": 0,
    "sru": 0
  }
}
```

<h3 id="get__nodes_{node_id}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[explorer.node](#schemaexplorer.node)|

<aside class="success">
This operation does not require authentication
</aside>

## get__stats

> Code samples

```shell
# You can also use wget
curl -X GET /stats \
  -H 'Accept: application/json'

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('/stats', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/stats',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /stats`

*Show stats about the grid*

Get statistics about the grid

<h3 id="get__stats-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|status|query|string|false|Node status filter, up/down.|

> Example responses

> 200 Response

```json
[
  {
    "accessNodes": 0,
    "contracts": 0,
    "countries": 0,
    "farms": 0,
    "gateways": 0,
    "nodes": 0,
    "publicIps": 0,
    "totalCru": 0,
    "totalHru": 0,
    "totalMru": 0,
    "totalSru": 0,
    "twins": 0
  }
]
```

<h3 id="get__stats-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|

<h3 id="get__stats-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[db.Counters](#schemadb.counters)]|false|none|none|
|» accessNodes|integer|false|none|none|
|» contracts|integer|false|none|none|
|» countries|integer|false|none|none|
|» farms|integer|false|none|none|
|» gateways|integer|false|none|none|
|» nodes|integer|false|none|none|
|» publicIps|integer|false|none|none|
|» totalCru|integer|false|none|none|
|» totalHru|integer|false|none|none|
|» totalMru|integer|false|none|none|
|» totalSru|integer|false|none|none|
|» twins|integer|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## get__twins

> Code samples

```shell
# You can also use wget
curl -X GET /twins \
  -H 'Accept: application/json'

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('/twins', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/twins',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /twins`

*Show twins on the grid*

Get all twins on the grid, It has pagination

<h3 id="get__twins-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|page|query|integer|false|Page number|
|size|query|integer|false|Max result per page|
|ret_count|query|string|false|Set farms' count on headers based on filter|
|twin_id|query|integer|false|twin id|
|account_id|query|string|false|account address|

> Example responses

> 200 Response

```json
[
  {
    "certificationType": "string",
    "dedicated": true,
    "farmId": 0,
    "name": "string",
    "pricingPolicyId": 0,
    "publicIps": [
      {
        "contractId": 0,
        "farmId": "string",
        "gateway": "string",
        "id": "string",
        "ip": "string"
      }
    ],
    "stellarAddress": "string",
    "twinId": 0
  }
]
```

<h3 id="get__twins-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|

<h3 id="get__twins-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[explorer.farm](#schemaexplorer.farm)]|false|none|none|
|» certificationType|string|false|none|none|
|» dedicated|boolean|false|none|none|
|» farmId|integer|false|none|none|
|» name|string|false|none|none|
|» pricingPolicyId|integer|false|none|none|
|» publicIps|[[db.PublicIP](#schemadb.publicip)]|false|none|none|
|»» contractId|integer|false|none|none|
|»» farmId|string|false|none|none|
|»» gateway|string|false|none|none|
|»» id|string|false|none|none|
|»» ip|string|false|none|none|
|» stellarAddress|string|false|none|none|
|» twinId|integer|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="grid-proxy-server-api-ping">ping</h1>

## get__ping

> Code samples

```shell
# You can also use wget
curl -X GET /ping \
  -H 'Accept: application/json'

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('/ping', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/ping',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /ping`

*ping the server*

ping the server to check if it running

> Example responses

> 200 Response

```json
"string"
```

<h3 id="get__ping-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|pong|string|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="grid-proxy-server-api-rmb">RMB</h1>

## post__twin_{twin_id}

> Code samples

```shell
# You can also use wget
curl -X POST /twin/{twin_id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('/twin/{twin_id}', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "cmd": "zos.statistics.get",
  "dat": "",
  "dst": [
    0
  ],
  "err": "",
  "exp": 0,
  "now": 1631078674,
  "ret": "",
  "shm": "",
  "src": 1,
  "try": 2,
  "uid": "",
  "ver": 1
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('/twin/{twin_id}',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`POST /twin/{twin_id}`

*submit the message*

submit the message

> Body parameter

```json
{
  "cmd": "zos.statistics.get",
  "dat": "",
  "dst": [
    0
  ],
  "err": "",
  "exp": 0,
  "now": 1631078674,
  "ret": "",
  "shm": "",
  "src": 1,
  "try": 2,
  "uid": "",
  "ver": 1
}
```

<h3 id="post__twin_{twin_id}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|twin_id|path|integer|true|twin id|
|body|body|[rmbproxy.Message](#schemarmbproxy.message)|true|rmb.Message|

> Example responses

> 200 Response

```json
{
  "retqueue": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
}
```

<h3 id="post__twin_{twin_id}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[rmbproxy.MessageIdentifier](#schemarmbproxy.messageidentifier)|

<aside class="success">
This operation does not require authentication
</aside>

## get__twin_{twin_id}_{retqueue}

> Code samples

```shell
# You can also use wget
curl -X GET /twin/{twin_id}/{retqueue} \
  -H 'Accept: application/json'

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('/twin/{twin_id}/{retqueue}', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/twin/{twin_id}/{retqueue}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /twin/{twin_id}/{retqueue}`

*Get the message result*

Get the message result

<h3 id="get__twin_{twin_id}_{retqueue}-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|twin_id|path|integer|true|twin id|
|retqueue|path|string|true|message retqueue|

> Example responses

> 200 Response

```json
[
  {
    "cmd": "zos.statistics.get",
    "dat": "",
    "dst": [
      0
    ],
    "err": "",
    "exp": 0,
    "now": 1631078674,
    "ret": "",
    "shm": "",
    "src": 1,
    "try": 2,
    "uid": "",
    "ver": 1
  }
]
```

<h3 id="get__twin_{twin_id}_{retqueue}-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|

<h3 id="get__twin_{twin_id}_{retqueue}-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[rmbproxy.Message](#schemarmbproxy.message)]|false|none|none|
|» cmd|string|false|none|none|
|» dat|string|false|none|none|
|» dst|[integer]|false|none|none|
|» err|string|false|none|none|
|» exp|integer|false|none|none|
|» now|integer|false|none|none|
|» ret|string|false|none|none|
|» shm|string|false|none|none|
|» src|integer|false|none|none|
|» try|integer|false|none|none|
|» uid|string|false|none|none|
|» ver|integer|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

<h2 id="tocS_db.Capacity">db.Capacity</h2>
<!-- backwards compatibility -->
<a id="schemadb.capacity"></a>
<a id="schema_db.Capacity"></a>
<a id="tocSdb.capacity"></a>
<a id="tocsdb.capacity"></a>

```json
{
  "cru": 0,
  "hru": 0,
  "mru": 0,
  "sru": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|cru|integer|false|none|none|
|hru|integer|false|none|none|
|mru|integer|false|none|none|
|sru|integer|false|none|none|

<h2 id="tocS_db.ContractBilling">db.ContractBilling</h2>
<!-- backwards compatibility -->
<a id="schemadb.contractbilling"></a>
<a id="schema_db.ContractBilling"></a>
<a id="tocSdb.contractbilling"></a>
<a id="tocsdb.contractbilling"></a>

```json
{
  "amountBilled": 0,
  "discountReceived": "string",
  "timestamp": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|amountBilled|integer|false|none|none|
|discountReceived|string|false|none|none|
|timestamp|integer|false|none|none|

<h2 id="tocS_db.Counters">db.Counters</h2>
<!-- backwards compatibility -->
<a id="schemadb.counters"></a>
<a id="schema_db.Counters"></a>
<a id="tocSdb.counters"></a>
<a id="tocsdb.counters"></a>

```json
{
  "accessNodes": 0,
  "contracts": 0,
  "countries": 0,
  "farms": 0,
  "gateways": 0,
  "nodes": 0,
  "publicIps": 0,
  "totalCru": 0,
  "totalHru": 0,
  "totalMru": 0,
  "totalSru": 0,
  "twins": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|accessNodes|integer|false|none|none|
|contracts|integer|false|none|none|
|countries|integer|false|none|none|
|farms|integer|false|none|none|
|gateways|integer|false|none|none|
|nodes|integer|false|none|none|
|publicIps|integer|false|none|none|
|totalCru|integer|false|none|none|
|totalHru|integer|false|none|none|
|totalMru|integer|false|none|none|
|totalSru|integer|false|none|none|
|twins|integer|false|none|none|

<h2 id="tocS_db.PublicConfig">db.PublicConfig</h2>
<!-- backwards compatibility -->
<a id="schemadb.publicconfig"></a>
<a id="schema_db.PublicConfig"></a>
<a id="tocSdb.publicconfig"></a>
<a id="tocsdb.publicconfig"></a>

```json
{
  "domain": "string",
  "gw4": "string",
  "gw6": "string",
  "ipv4": "string",
  "ipv6": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|domain|string|false|none|none|
|gw4|string|false|none|none|
|gw6|string|false|none|none|
|ipv4|string|false|none|none|
|ipv6|string|false|none|none|

<h2 id="tocS_db.PublicIP">db.PublicIP</h2>
<!-- backwards compatibility -->
<a id="schemadb.publicip"></a>
<a id="schema_db.PublicIP"></a>
<a id="tocSdb.publicip"></a>
<a id="tocsdb.publicip"></a>

```json
{
  "contractId": 0,
  "farmId": "string",
  "gateway": "string",
  "id": "string",
  "ip": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|contractId|integer|false|none|none|
|farmId|string|false|none|none|
|gateway|string|false|none|none|
|id|string|false|none|none|
|ip|string|false|none|none|

<h2 id="tocS_explorer.contract">explorer.contract</h2>
<!-- backwards compatibility -->
<a id="schemaexplorer.contract"></a>
<a id="schema_explorer.contract"></a>
<a id="tocSexplorer.contract"></a>
<a id="tocsexplorer.contract"></a>

```json
{
  "billing": [
    {
      "amountBilled": 0,
      "discountReceived": "string",
      "timestamp": 0
    }
  ],
  "contractId": 0,
  "created_at": 0,
  "details": null,
  "state": "string",
  "twinId": 0,
  "type": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|billing|[[db.ContractBilling](#schemadb.contractbilling)]|false|none|none|
|contractId|integer|false|none|none|
|created_at|integer|false|none|none|
|details|any|false|none|none|
|state|string|false|none|none|
|twinId|integer|false|none|none|
|type|string|false|none|none|

<h2 id="tocS_explorer.farm">explorer.farm</h2>
<!-- backwards compatibility -->
<a id="schemaexplorer.farm"></a>
<a id="schema_explorer.farm"></a>
<a id="tocSexplorer.farm"></a>
<a id="tocsexplorer.farm"></a>

```json
{
  "certificationType": "string",
  "dedicated": true,
  "farmId": 0,
  "name": "string",
  "pricingPolicyId": 0,
  "publicIps": [
    {
      "contractId": 0,
      "farmId": "string",
      "gateway": "string",
      "id": "string",
      "ip": "string"
    }
  ],
  "stellarAddress": "string",
  "twinId": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|certificationType|string|false|none|none|
|dedicated|boolean|false|none|none|
|farmId|integer|false|none|none|
|name|string|false|none|none|
|pricingPolicyId|integer|false|none|none|
|publicIps|[[db.PublicIP](#schemadb.publicip)]|false|none|none|
|stellarAddress|string|false|none|none|
|twinId|integer|false|none|none|

<h2 id="tocS_explorer.location">explorer.location</h2>
<!-- backwards compatibility -->
<a id="schemaexplorer.location"></a>
<a id="schema_explorer.location"></a>
<a id="tocSexplorer.location"></a>
<a id="tocsexplorer.location"></a>

```json
{
  "city": "string",
  "country": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|city|string|false|none|none|
|country|string|false|none|none|

<h2 id="tocS_explorer.node">explorer.node</h2>
<!-- backwards compatibility -->
<a id="schemaexplorer.node"></a>
<a id="schema_explorer.node"></a>
<a id="tocSexplorer.node"></a>
<a id="tocsexplorer.node"></a>

```json
{
  "certificationType": "string",
  "city": "string",
  "country": "string",
  "created": 0,
  "dedicated": true,
  "farmId": 0,
  "farmingPolicyId": 0,
  "gridVersion": 0,
  "id": "string",
  "location": {
    "city": "string",
    "country": "string"
  },
  "nodeId": 0,
  "publicConfig": {
    "domain": "string",
    "gw4": "string",
    "gw6": "string",
    "ipv4": "string",
    "ipv6": "string"
  },
  "rentContractId": 0,
  "rentedByTwinId": 0,
  "status": "string",
  "total_resources": {
    "cru": 0,
    "hru": 0,
    "mru": 0,
    "sru": 0
  },
  "twinId": 0,
  "updatedAt": 0,
  "uptime": 0,
  "used_resources": {
    "cru": 0,
    "hru": 0,
    "mru": 0,
    "sru": 0
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|certificationType|string|false|none|none|
|city|string|false|none|none|
|country|string|false|none|none|
|created|integer|false|none|none|
|dedicated|boolean|false|none|none|
|farmId|integer|false|none|none|
|farmingPolicyId|integer|false|none|none|
|gridVersion|integer|false|none|none|
|id|string|false|none|none|
|location|[explorer.location](#schemaexplorer.location)|false|none|none|
|nodeId|integer|false|none|none|
|publicConfig|[db.PublicConfig](#schemadb.publicconfig)|false|none|none|
|rentContractId|integer|false|none|none|
|rentedByTwinId|integer|false|none|none|
|status|string|false|none|added node status field for up or down|
|total_resources|[db.Capacity](#schemadb.capacity)|false|none|none|
|twinId|integer|false|none|none|
|updatedAt|integer|false|none|none|
|uptime|integer|false|none|none|
|used_resources|[db.Capacity](#schemadb.capacity)|false|none|none|

<h2 id="tocS_rmbproxy.Message">rmbproxy.Message</h2>
<!-- backwards compatibility -->
<a id="schemarmbproxy.message"></a>
<a id="schema_rmbproxy.Message"></a>
<a id="tocSrmbproxy.message"></a>
<a id="tocsrmbproxy.message"></a>

```json
{
  "cmd": "zos.statistics.get",
  "dat": "",
  "dst": [
    0
  ],
  "err": "",
  "exp": 0,
  "now": 1631078674,
  "ret": "",
  "shm": "",
  "src": 1,
  "try": 2,
  "uid": "",
  "ver": 1
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|cmd|string|false|none|none|
|dat|string|false|none|none|
|dst|[integer]|false|none|none|
|err|string|false|none|none|
|exp|integer|false|none|none|
|now|integer|false|none|none|
|ret|string|false|none|none|
|shm|string|false|none|none|
|src|integer|false|none|none|
|try|integer|false|none|none|
|uid|string|false|none|none|
|ver|integer|false|none|none|

<h2 id="tocS_rmbproxy.MessageIdentifier">rmbproxy.MessageIdentifier</h2>
<!-- backwards compatibility -->
<a id="schemarmbproxy.messageidentifier"></a>
<a id="schema_rmbproxy.MessageIdentifier"></a>
<a id="tocSrmbproxy.messageidentifier"></a>
<a id="tocsrmbproxy.messageidentifier"></a>

```json
{
  "retqueue": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|retqueue|string|false|none|none|

