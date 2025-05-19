# 🧠 Intelligent Sales Analysis of Fashion Products using NLP and Feature Clustering

This project applies Natural Language Processing (NLP) and structured attribute grouping to identify and analyze the most frequently sold combinations of clothing products.

Fashion items are notoriously diverse and often subject to trends and constant model updates. Relying on exact product names for sales analysis becomes inefficient because:

- Similar items may appear under different names
- Product names may include non-informative or inconsistent parts (like brand, year, batch)
- Exact SKUs may go out of production, but the style remains in demand

This pipeline is designed to overcome these limitations by extracting meaningful features and grouping sales based on actual product characteristics.

---

## ✨ Key Features

The script performs two levels of automated sales analysis:

### 1. 🧠 Keyword-Based NLP Clustering

- Uses Hazm for Persian NLP: tokenization and normalization
- Extracts important tokens (n-grams) from product names using TF-IDF
- Clusters similar items using KMeans based on linguistic patterns
- Assigns the most representative keywords to each cluster
- Aggregates total sales (`ordered_qty`) per keyword cluster

⬇️ Output: `output_keywords_clustering.xlsx`

| Extracted Keyword Label       | Type     | Total Sales |
|------------------------------|----------|-------------|
| تی شرت مردانه کوتاه           | T-shirt  | 1,250       |
| پیراهن زنانه بلند             | Shirt    | 900         |

---

### 2. 📊 Feature-Based Grouping from Structured Data

- Combines structured fields: `Gender`, `Type`, `Color`, `Material`
- Creates a standardized product feature label
- Groups logically similar items regardless of naming
- Aggregates total sales across these meaningful combinations

⬇️ Output: `output_combination_clustering.xlsx`

| Combined Feature Label              | Type     | Total Sales |
|------------------------------------|----------|-------------|
| T-shirt Men Blue Cotton            | T-shirt  | 1,520       |
| Pants Women Black Polyester        | Pants    | 870         |

---

## 📂 Input Requirements

The input file should be an Excel sheet named `products.xlsx` with the following columns:

- `Product name` – the full name/title of the product (text, Persian)
- `ordered_qty` – number of orders/sales
- `Gender`       – structured gender data (e.g., مردانه, زنانه)
- `Type`         – clothing type (e.g., تی شرت, شلوار, پیراهن)
- `Color`        – color name (e.g., آبی, سفید)
- `Material`     – fabric material (e.g., نخی, پلی استر)

---

## ⚙️ Installation

Make sure you install the following packages:

```bash
pip install pandas scikit-learn hazm numpy openpyxl
