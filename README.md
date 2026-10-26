# Advertising fake API

Daily ad spend for six stores (A–F), 2026-01-01 to 2026-10-10 — 1,698 rows.
Columns: `store`, `day`, `ad_spend`.

## Endpoints

| What | URL |
|---|---|
| CSV | https://raw.githubusercontent.com/franciellessantos/advertising-api/main/ADVERTISING.csv |
| JSON (all rows) | https://raw.githubusercontent.com/franciellessantos/advertising-api/main/advertising.json |
| REST-style (filters) | https://my-json-server.typicode.com/franciellessantos/advertising-api/advertising |

The REST-style endpoint (served by [My JSON Server](https://my-json-server.typicode.com) from `db.json`) supports query filters, e.g.
`/advertising?store=A`, `/advertising?day=2026-02-14`, `/advertising/1`.

## Python

```python
import requests
import pandas as pd

# Like calling an API: get JSON
url = "https://raw.githubusercontent.com/franciellessantos/advertising-api/main/advertising.json"
data = requests.get(url, timeout=30).json()
df = pd.DataFrame(data)

# Or read the CSV directly
df = pd.read_csv("https://raw.githubusercontent.com/franciellessantos/advertising-api/main/ADVERTISING.csv")

# Filtered request (store A only)
store_a = requests.get(
    "https://my-json-server.typicode.com/franciellessantos/advertising-api/advertising",
    params={"store": "A"}, timeout=30,
).json()
```
