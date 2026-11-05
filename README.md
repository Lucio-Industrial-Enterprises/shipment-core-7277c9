# Warehouse tools

Small Python utilities for warehouse order and shipping workflows.

Run the tests with `python3 -m unittest discover -s tests -v`.

## Shipping

`shipping_quote(weight_kg, zone, service="standard")` returns a shipping quote
in dollars.

- **Zones**: `local` (base $5) or `regional` (base $8); weight must be positive.
- **Services**: `standard` (default) or `express` ($7 surcharge over standard).

```python
from warehouse.rates import shipping_quote

shipping_quote(2, "local")               # 8.0  — standard local
shipping_quote(2, "local", "express")    # 15.0 — express local
shipping_quote(2, "regional", "express") # 18.0 — express regional
```

The command-line entry point accepts an optional `--service` flag:

```
python -m warehouse.cli 2 local
python -m warehouse.cli 2 local --service express
```
