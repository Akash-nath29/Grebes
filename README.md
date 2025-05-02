
![grebes_banner_fixed](https://github.com/user-attachments/assets/f172f0df-a198-44cf-97a2-50ca9b06aa36)

# Grebes

🕵️‍♂️ **Grebes** — A lightweight, nature-inspired data quality auditor for structured datasets.

---

## 🚀 Features

- **Fast, zero-config audit** of CSV, Excel (`.xls`/`.xlsx`), JSON and JSON-Lines files
- **Rich CLI output** with colored panels, sparklines, and warnings (powered by [Rich](https://github.com/Textualize/rich))
- **Key data quality checks**:
  - Missing value counts & percentages
  - Unique-value ratio & (optional) samples
  - Numeric statistics (mean, std, min, max) & IQR-based outlier counts
  - Inline histograms (sparklines) for numeric distributions
  - Date-range for datetime columns
  - Top-N frequencies for low-cardinality text/categorical columns
  - Mixed-type detection & duplicate-row warnings
- **Two modes**:
  - **CLI**: `grebes data.csv` → instant terminal report
  - **Python API**: import `GrebesAuditor` into notebooks or scripts

---

## 💾 Installation

```bash
# From PyPI (when published)
pip install grebes

# Or install your local copy in editable mode for development
git clone https://github.com/yourusername/grebes.git
cd grebes
pip install -e .
````

> **Requires** Python ≥ 3.7 and the following packages:
> `pandas`, `numpy`, `openpyxl` (for Excel), and `rich`.

---

## ⚡ CLI Usage

```bash
# Basic audit of a CSV file
grebes data.csv

# Audit an Excel sheet
grebes report.xlsx

# Audit a JSON-Lines file
grebes records.jsonl

# Show help / available options
grebes --help
```

### Sample Output

<details>
<summary>Click to expand</summary>

```
╭────────────────────────────── 🧠 GREBES DIAGNOSTIC REPORT ──────────────────────────────╮
│ Rows: 1,000   Cols: 5   Mem: 180.21 KB                                                  │
╰─────────────────────────────────────────────────────────────────────────────────────────╯

╭──── id ─────────────────────────────────────────────────────────────────────────╮
│ Type    int64                                                                   │
│ Missing 0 (0.0%)                                                                │
│ Unique  1000                                                                    │
│ Stats   μ=500.5,σ=288.8,min=1.0,max=1000.0,out=0                                │
│ Dist    █▁▂▃▄▅▆▇█
╰─────────────────────────────────────────────────────────────────────────────────╯

╭─── amount ───────────────────────────────────────────────────────────────────────╮
│ Type    float64                                                                  │
│ Missing 0 (0.0%)                                                                 │
│ Stats   μ=495.4,σ=289.2,min=14.6,max=999.7,out=0                                 │
│ Dist    ▁▃▄▅▇▆▇▅                                                               │
╰──────────────────────────────────────────────────────────────────────────────────╯

… and so on for each column …

```

</details>

---

## 📦 Python API

```python
import pandas as pd
from grebes.auditor import GrebesAuditor

df = pd.read_csv("data.csv")
auditor = GrebesAuditor(df)
auditor.print_report()
```

---

## 📝 How It Works

1. **Reads** your file (CSV, Excel, JSON(.l)) into a `pandas.DataFrame`.
2. **Computes** column-wise metrics:

   * Missing values
   * Unique ratio (and optional sample values for low-cardinality columns)
   * Descriptive stats & outlier count for numerics
   * Date ranges for datetimes
   * Top frequencies for text/categorical
3. **Renders** an interactive, colorized report with:

   * **Panels** per column
   * **Sparklines** for quick distribution glance
   * **Warnings** for mixed-type columns & duplicates
4. **Zero external calls** — all local, so safe on private data.

---

## 🤝 Contributing

1. Fork the repo
2. Create a feature branch: `git checkout -b feat/my-awesome-feature`
3. Commit your changes: `git commit -m "Add feature X"`
4. Push to your branch: `git push origin feat/my-awesome-feature`
5. Open a Pull Request

Please follow the existing code style and add tests for new functionality.

---

## 📜 License

MIT License © Your Name
See [LICENSE](LICENSE) for details.

---

> Built with 💙 and inspired by nature’s grace—light as air, sharp as a grebe’s dive.
