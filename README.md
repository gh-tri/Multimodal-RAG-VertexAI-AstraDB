# Multimodal RAG with Vertex AI and Astra DB

A simple learning project that shows how to build a **multimodal Retrieval-Augmented Generation (RAG)** pipeline using:

- **Google Vertex AI / Gemini**
- **Astra DB (Cassandra)**

The project takes an input image, retrieves similar products from a vector database, and then uses Gemini 2.5 pro to generate a grounded answer using both the image and the retrieved catalog context.

## Project idea

This notebook demonstrates a small **visual product/component retrieval** workflow.

Example flow:

1. Provide an image of a product or component
2. Generate an embedding for the image
3. Store and search product embeddings in Astra DB
4. Retrieve the most similar products
5. Pass the image + retrieved product context to Gemini
6. Generate a grounded response with likely product name, replacement suggestions, and related details


## Use case

A practical use case is a **replacement part finder**.

For example:
- upload a coffee machine component image
- retrieve visually similar products from a catalog
- ask Gemini to explain what the part is
- suggest possible replacement products with price / URL from retrieved results

The same logic can be extended to:
- spare part search
- hardware/component lookup
- catalog search from images
- visual product recommendation

## Files

```text
.
├── Multimodal_RAG_VertexAI_GCP_Langchain_cleaned.ipynb
├── README.md
└── requirements.txt
```

## Requirements

You will need:

- a Google Cloud project with Vertex AI enabled
- authenticated access to GCP
- an Astra DB database / token
- environment variables or notebook prompts for credentials
