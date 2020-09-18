ReftabPython
=============

This is a quick and dirty module to interact with the Reftab API via Python.

# Instructions

### Download repository

Use the [Reftab API documentation](https://www.reftab.com/api-docs) to find endpoints to access.

### Methods
The ReftabClient has 4 methods available, get, post, put, delete, corresponding to the HTTP methods.

Parameters each take:
* get(endpoint, id)
  * endpoint (e.g. assets, optional parameters may be added such as ?limit=200 to get additional assets)
  * id (default None)
* post(endpoint, body)
  * endpoint (e.g. assets)
  * body (a python dictionary which will be converted to json)
* put(endpoint, id, body)
  * endpoint (e.g. assets)
  * id (required)
  * body (a python dictionary which will be converted to json)
* delete(endpoint, id)
  * endpoint (e.g. assets)
  * id (required)

### Prerequisites

* Python 3 or later
* A valid API key pair from Reftab
  * Generate one in Reftab Settings
  
# Examples

### Get an Asset and Update It

```python
#This example shows how to get an asset and update it

from reftab import ReftabClient

client = ReftabClient(
    secretKey=[secretKey],
    publicKey=[publicKey]
)

asset = client.get('assets', 'NY00')

asset['title'] = 'New Title'

client.post('assets', asset)
```