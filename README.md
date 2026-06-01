# computesphere-python

The official Python SDK for the [ComputeSphere](https://computesphere.com) API.

## Install

```bash
pip install computesphere-api-client
```

Python 3.10+.

## Authentication

The client authenticates with a **ComputeSphere access token** — either an
**API token** (create one in the [console](https://console.computesphere.com)
under **Settings → API Tokens**) or an **OAuth access token**.

## Usage

```python
import os
from computesphere_api_client import AuthenticatedClient
from computesphere_api_client.api.regions import list_regions

client = AuthenticatedClient(
    base_url="https://api.computesphere.com/api/v2",
    token=os.environ["COMPUTESPHERE_API_TOKEN"],
)

response = list_regions.sync_detailed(client=client, x_account_id=account_id)

if response.parsed is None:
    print(f"HTTP {response.status_code}")
else:
    for region in response.parsed.items:
        print(region.name, region.display_name)
```

## Documentation

Full API reference: <https://docs.computesphere.com>.

## License

[Apache-2.0](./LICENSE). ComputeSphere is a trademark of ComputeSphere LLC.
