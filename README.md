# Amazon ETL Semantic Search

## Project Description

This project demonstrates a simple **ETL (Extract, Transform, Load)** pipeline and **semantic search** on Amazon product data using Python. The aim is to show how raw product data can be cleaned, processed, converted into vector embeddings, and searched using natural language queries.

The entire implementation is done in a single Google Colab Notebook for ease of understanding and evaluation, making it suitable for **college-level coursework or mini projects**.

---

## Dataset

* Source file: `amazon.csv`
* Format: CSV
* Key columns used in this project:

  * `product_id`
  * `product_name`
  * `about_product`

Only the relevant columns are selected to keep the project focused and lightweight.

---

## Tools & Libraries Used

* **Python 3**
* **Pandas** – data loading and preprocessing
* **SentenceTransformers** – text embedding generation
* **FAISS** – vector similarity search
* **Google Colab** – development and execution

---

## ETL Workflow

### 1. Extract

* Load Amazon product data from `amazon.csv` using Pandas
* Inspect data shape and preview records

### 2. Transform

* Select only required columns
* Remove duplicate records
* Prepare text data (`about_product`) for embedding

### 3. Load

* Convert product descriptions into numerical embeddings using a pre-trained **SentenceTransformer model**
* Store embeddings in a **FAISS IndexFlatL2** vector index for fast similarity search

---

## Semantic Search Implementation

* Each product description is converted into a vector embedding
* User queries are also converted into embeddings
* FAISS computes similarity between query and product vectors
* Top matching products are returned based on distance

Example function used in the notebook:

* `semantic_search(query, k=5)`

This returns the most relevant products for a given natural language query.

---

## How to Run the Project (Google Colab)

1. Open **Google Colab**

   * Go to: [https://colab.research.google.com](https://colab.research.google.com)

2. Upload the notebook

   * Click **File → Upload notebook**
   * Upload `Amazon_ETL_Semantic_Search.ipynb`

3. Upload the dataset

   * In the left panel, click **Files → Upload**
   * Upload `amazon.csv`

4. Install required libraries

```python
!pip install pandas sentence-transformers faiss-cpu
```

5. Run the notebook

   * Execute each cell from top to bottom

The semantic search results will be displayed directly in the notebook output.

---

## Sample Query

```text
"wireless bluetooth headphones"
```

The system retrieves products with similar meaning even if exact keywords do not match.

---
