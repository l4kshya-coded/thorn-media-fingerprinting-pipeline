# Thorn Media Fingerprinting & Automated Triage Pipeline

A robust, Python-based computer vision and trust-and-safety moderation pipeline simulating **Thorn's Spotlight** architecture. This repository implements perceptual hashing (`phash`) and multi-tier Hamming distance matching to securely fingerprint, detect, quarantine, and audit incoming visual media for exploitation prevention frameworks.

---

## 🚀 Features
* **Perceptual Fingerprinting:** Utilizes `imagehash` and `Pillow` to generate robust image signatures resilient to compression, resizing, and minor modifications.
* **Multi-Tier Hamming Distance Triage:** Evaluates similarity scores against known reference databases to automatically route media into strict security tiers:
  * *Critical Quarantine:* Instant quarantine and account flagging for high-confidence matches.
  * *Review Queue:* Suspicious or modified media forwarded to human trust-and-safety teams.
  * *Clean Passed:* Safe media cleared for normal delivery.
* **Automated Audit Logging:** Compiles timestamped incident reports and exports structured compliance CSVs (`moderation_incident_audit.csv`) for investigative review.

---

## 🛠️ Tech Stack
* **Language:** Python 3
* **Environment:** Google Colab / Local Jupyter
* **Libraries:** `imagehash`, `Pillow`, `pandas`, `numpy`, `matplotlib`

---

## 📊 Pipeline Architecture
```text
[Incoming Media Batch] 
       │
       ▼
[Perceptual Hashing (phash)] 
       │
       ▼
[Hamming Distance Matrix Matching] 
       ├── (Distance ≤ 3)  ──► [Critical Quarantine & Flag]
       ├── (Distance ≤ 7)  ──► [Review Queue (Trust & Safety)]
       └── (Distance > 7)  ──► [Clean Passed / Normal Delivery]
       │
       ▼
[Structured CSV Audit Log Generation]
```

---

## 💻 Quickstart (Google Colab)
1. Open [Google Colab](https://colab.research.google.com/) and create a new notebook.
2. Install dependencies:
   ```python
   !pip install Pillow imagehash matplotlib numpy pandas
   ```
3. Copy and run the pipeline cells to execute reference database simulation, batch ingestion, threat categorization, and audit log generation.