# Advertising fake API

Daily ad spend for six stores (A–F), 2026-01-01 to 2026-10-10 — 1,698 rows.
Columns: `store`, `day`, `ad_spend`.

## Endpoints

| What | URL |
|---|---|
| CSV | https://raw.githubusercontent.com/franciellessantos/advertising-api/main/ADVERTISING.csv |
| JSON (all rows) | https://raw.githubusercontent.com/franciellessantos/advertising-api/main/advertising.json |

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

# Filter like an API query (store A only)
store_a = [row for row in data if row["store"] == "A"]
```
