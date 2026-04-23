# Multimodal RAG with Vertex AI & Astra DB

This notebook demonstrates an end-to-end **multimodal Retrieval-Augmented Generation (RAG)** pipeline. Given a photo of an unknown coffee machine part, the system finds visually similar products from a catalog and uses Gemini to generate a grounded, natural-language answer with product names, prices, and purchase links.

---

## How It Works

1. **Sanity checks** — verify Gemini handles both text and image prompts correctly
2. **Build a product catalog** — a small in-memory dataset of Breville espresso machine parts (name, price, image URL, product URL)
3. **Embed the catalog** — generate 1408-dimensional image embeddings for each product using `multimodalembedding@001`
4. **Store in Astra DB** — persist all vectors and metadata in an Astra DB vector collection
5. **Embed the query image** — encode the uploaded test image with the same model
6. **Vector search** — retrieve the top-3 most similar products from Astra DB
7. **Generate an answer** — pass the query image + retrieved context to Gemini for a grounded response

---

## Stack

| Component | Role |
|---|---|
| [Vertex AI](https://cloud.google.com/vertex-ai) | Gemini 2.5 Pro (generation) + `multimodalembedding@001` (embeddings) |
| [Astra DB](https://www.datastax.com/products/datastax-astra) | Vector store (1408-dim collection) |
| [RAGStack](https://docs.datastax.com/en/ragstack/index.html) | Astra DB Python client (`astrapy`) |
| Google Colab | Notebook runtime |

---

## Prerequisites
- A **GCP project** with Vertex AI API enabled
- An **Astra DB** account with a database endpoint and token
- Python 3.9+
- A **GCP project** with Vertex AI API enabled
- An **Astra DB** account with a database endpoint and token
- Python 3.9+
