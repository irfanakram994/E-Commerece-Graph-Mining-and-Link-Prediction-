# E-Commerce Graph Mining & Link Prediction 🚀

An end-to-end, resource-optimized data mining pipeline that extracts topological features from product co-purchasing networks to predict latent product relationships. Built entirely to run seamlessly within cloud-hosted environments like the free tier of Google Colab.

## 🔗 Live Execution Link
You can review, audit, and execute this entire data mining pipeline with a single click:
👉 **[CLICK HERE TO OPEN THE LIVE GOOGLE COLAB NOTEBOOK](https://colab.research.google.com/drive/1Znt0D0cUazmwOgui30k7_tZ_rKp1TEes?usp=sharing)** 
*(Note: Please replace the placeholder above with your actual Colab Share link containing viewer permissions.)*

---

## 🛠️ System Architecture & Data Pipeline

The pipeline is fully automated and self-contained, executing across seven distinct data-mining steps:

### 1. Automated Session Ingestion
* Handles server-side automated download security blocks by passing synthetic `User-Agent` headers.
* Streams and decompresses the **Stanford SNAP Amazon Co-purchasing Network Dataset** completely inside volatile environment RAM with no Google Drive storage dependencies.

### 2. Algorithmic RAM Filtering & Subgraph Slicing
* The original dataset contains over 400,000 entities. To strictly respect hardware limitations (Colab's free 12GB RAM limit), a dense structural subgraph is dynamically extracted.
* **Output:** A stabilized, highly correlated network consisting of **3,000 unique nodes** and **8,989 structural edges**.

### 3. Balanced Dataset Preparation
* Link prediction requires a binary classification target matrix.
* **Positive Samples (Label 1):** The 8,989 real-world observed product connections.
* **Negative Samples (Label 0):** An equivalent number of randomly generated node-pairs that have never co-occurred, protecting the model against severe class-imbalance bias.

### 4. Topological Feature Mining
Instead of utilizing text metadata, the pipeline engineers pure mathematical structural features by calculating local neighborhood overlaps:
* **Jaccard Coefficient:** Measures relative common neighborhood size.
* **Resource Allocation Index:** Measures the closeness of mutual neighbors weighted inversely by their degrees.
* **Adamic-Adar Index:** Fosters prediction confidence by penalizing high-degree common elements.

### 5. Prediction Modelling & Classifier Execution
* Features are isolated and partitioned using a 70/30 train-test split.
* A **Random Forest Classifier** is executed to map neighborhood metrics directly to link probabilities.

### 6. Interactive Network Visualization
* Isolates localized dense subgraphs dynamically to draw structural maps without performance throttling.
* Generates clear visual markers to distinguish verified buying arcs (Solid Blue Arcs) from target prediction candidates (Dashed Crimson Pathing).

---

## 📈 Empirical Performance Evaluation

The automated pipeline yields highly precise results upon completion:

* **ROC-AUC Accuracy Score:** `0.9286` (92.86% probability accuracy)
* **Weighted F1-Score:** `0.93`

### Comprehensive Classification Breakdown:
```text
              precision    recall  f1-score   support

           0       0.88      0.99      0.93      2718
           1       0.99      0.86      0.92      2676

    accuracy                           0.93      5394
```

---
## 🧑‍💻 How to Reproduce and Run
1. Open the **Google Colab** link provided in the execution section above.
2. Ensure your Colab Runtime is connected.
3. Click `Runtime` -> `Run all` (or press `Ctrl + F9`).
4. Scroll to the bottom of the cells to view live execution logs, accuracy metrics, and the generated network layout topology maps.
