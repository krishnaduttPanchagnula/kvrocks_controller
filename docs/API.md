
# HTTP APIs
## Namespace APIs
### Create Namespace

```shell
POST /api/v1/namespaces
```

#### Request Body

```json
{
  "namespace": "test-ns"
}
```

#### Response JSON Body

* 201
```json
{
  "data": "created"
}
```

* 409
```json
{
  "error": {
    "message": "the entry already existed"
  }
}
```

* 5XX
```json
{
  "error": {
    "message": "DETAIL ERROR STRING"
  }
}
```

### List Namespace
```shell
GET /api/v1/namespaces
```
#### Response JSON Body

* 200
```json
{
  "data": {
    "namespaces": ["test-ns"]
  }
}
```
* 5XX
```json
{
  "error": {
    "message": "DETAIL ERROR STRING"
  }
}
```

### Delete Namespace

```shell
GET /api/v1/namespaces/{namespace}
```

#### Response JSON Body

* 200
```json
{
  "data": "ok"
}
```

* 404
```json
{
  "error": {
    "message": "the entry does not exist"
  }
}

```

* 5XX
```json
{
  "error": {
    "message": "DETAIL ERROR STRING"
  }
}
```
## Cluster APIs
### Create Cluster

```
POST /api/v1/namespaces/{namespace}/clusters
```

#### Request Body

```json
{
  "name":"test-cluster",
  "nodes":["127.0.0.1:6666"],
  "replica":1,
  "password":""
}
```

#### Response JSON Body

* 201
```json
{
  "data": "created"
}
```

* 409
```json
{
  "error": {
    "message": "the entry already existed"
  }
}
```

* 5XX
```json
{
  "error": {
    "message": "DETAIL ERROR STRING"
  }
}
```

### List Cluster

```shell
GET /api/v1/namespaces/{namespace}/clusters
```
#### Response JSON Body

* 200
```json
{
  "data": {
    "clusters": ["test-cluster"]
  }
}
```

* 5XX
```json
{
  "error": {
    "message": "DETAIL ERROR STRING"
  }
}
```

### Get Cluster

```shell
GET /api/v1/namespaces/{namespace}/clusters/{cluster}
```

#### Response JSON Body

* 200
```json
{
  "data":
  {
    "cluster": {
      "name":"test-cluster",
      "version":0,
      "shards":[
        {"nodes":[
          {
            "id":"YotDSqzTeHK6CnIX2gZu27IlcYRTW4dkkFQvV382",
            "addr":"127.0.0.1:6666",
            "role":"master",
            "password":"",
            "master_auth":"",
            "created_at":16834433980
          }],
          "slot_ranges":["0-16383"],
          "import_slot":-1,
          "migrating_slot":-1
        }
      ]
    }
  }
}
```

* 404
```json
{
  "error": {
    "message": "the entry does not exist"
  }
}
```

* 5XX
```json
{
  "error": {
    "message": "DETAIL ERROR STRING"
  }
}
```

### Delete Cluster

```shell
DELETE /api/v1/namespaces/{namespace}/clusters/{cluster}
```

#### Response JSON Body

* 200
```json
{
  "data": "ok"
}
```

* 404
```json
{
  "error": {
    "message": "the entry does not exist"
  }
}
```

* 5XX
```json
{
  "error": {
    "message": "DETAIL ERROR STRING"
  }
}
```
## Shard APIs
### Create Shard 

```
POST /api/v1/namespaces/{namespace}/clusters/{cluster}/shards
```

#### Request Body

```json
{
  "nodes":["127.0.0.1:6666"],
  "password":""
}
```

#### Response JSON Body

* 201
```json
{
  "data": "created"
}
```

* 409
```json
{
  "error": {
    "message": "the entry already existed"
  }
}
```

* 5XX
```json
{
  "error": {
    "message": "DETAIL ERROR STRING"
  }
}
```


### Get Shard

```shell
GET /api/v1/namespaces/{namespace}/clusters/{cluster}/shards/{shard}
```

#### Response JSON Body

* 200
```json
{
  "data": {
    "shard": {
      "nodes": [
        {
          "id": "3SStZULMqclwvYNT8gN05IdybROe0vEnn97iNB5Z",
          "addr": "127.0.0.1:6666",
          "role": "master",
          "password": "",
          "master_auth": "",
          "created_at": 16834433980
        }
      ],
      "slot_ranges": [
        "0-16383"
      ],
      "import_slot": -1,
      "migrating_slot": -1
    }
  }
}

```

* 404
```json
{
  "error": {
    "message": "the entry does not exist"
  }
}
```

* 5XX
```json
{
  "error": {
    "message": "DETAIL ERROR STRING"
  }
}
```

### List Shard 

```shell
GET /api/v1/namespaces/{namespace}/clusters/{cluster}/shards
```
#### Response JSON Body

* 200
```json
{
  "data": {
    "shards": [
      {
        "nodes": [
          {
            "id": "3SStZULMqclwvYNT8gN05IdybROe0vEnn97iNB5Z",
            "addr": "127.0.0.1:6666",
            "role": "master",
            "password": "",
            "master_auth": "",
            "created_at": 16834433980
          }
        ],
        "slot_ranges": [
          "0-16383"
        ],
        "import_slot": -1,
        "migrating_slot": -1
      },
      {
        "nodes": [
          {
            "id": "y5PftTd0Lc3hH34yEyavIji86cRM5i3oxytt42vo",
            "addr": "127.0.0.1:6667",
            "role": "master",
            "password": "",
            "master_auth": "",
            "created_at": 16834433980
          }
        ],
        "slot_ranges": null,
        "import_slot": -1,
        "migrating_slot": -1
      }
    ]
  }
}

```

* 5XX
```json
{
  "error": {
    "message": "DETAIL ERROR STRING"
  }
}
```

### Delete Shard 

```shell
DELETE /api/v1/namespaces/{namespace}/clusters/{cluster}/shards/{shard}
```

#### Response JSON Body

* 200
```json
{
  "data": "ok"
}
```

* 404
```json
{
  "error": {
    "message": "the entry does not exist"
  }
}
```

* 5XX
```json
{
  "error": {
    "message": "DETAIL ERROR STRING"
  }
}
```