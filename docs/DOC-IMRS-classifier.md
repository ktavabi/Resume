# WADOC Incident Classification System

> **Context:** Work carried out at WADOC in partnership with [Recidiviz](https://recidiviz.org). Stack: Python, pandas, scikit-learn.

---

## Project Summary

Built an end-to-end **NLP-driven multi-label text classification system** that automatically classifies free-text correctional incident narrative reports into 73 binary incident categories, replacing a manual labeling process performed by corrections staff across all WADOC facilities (prisons, work-release centers, and field offices). The system reads the narrative description of each incident and predicts which incident types apply — with no human review required in the inference path.

---

## CV / Resume Bullet Points

- **Designed and deployed a production-ready multi-label NLP classifier** for Washington DOC's incident management system, automating classification of correctional incident reports across 73 incident type labels — achieving **75.6% F1 score**, **88.3% precision**, and **60.6% exact match accuracy** on ~28K held-out incidents, representing a **30× improvement over a random baseline**.

- **Built a full scikit-learn ML pipeline** (data ingestion → feature engineering → training → evaluation) over ~111K labeled incident records sourced from a 24-table relational database (Oracle/OMNI), exported as 9 flat CSV files and loaded with pandas for processing.

- **Engineered structured and unstructured features** from multi-table correctional records: concatenated multi-section narrative text fields, vectorized narratives using `TfidfVectorizer` (15K features, unigrams + bigrams, `sublinear_tf=True`), and aggregated participant-level features (age, injury flags, hospitalization flags) to the incident level via `groupby` + `agg`.

- **Implemented a one-vs-rest multi-label strategy** using scikit-learn's `MultiOutputClassifier` wrapping `LogisticRegression`, with one independent binary classifier per incident type; constructed multi-hot label targets using `pd.get_dummies` + `groupby(max)` aggregation across participant rows.

- **Performed systematic model diagnostics**: analyzed logistic regression weight distributions across all 15K vocabulary features (weight range [−3.2, +12.7]), identified the most predictive tokens per label (e.g., `transport`, `ambulance`, `hospital` → medical transport category; `prea`, `family`, `visitor` → negative predictors), and benchmarked against multiple baselines (all-negative, age-only, random).

- **Executed rigorous data quality and trainability assessment** using pandas: validated zero narrative missingness across 111K records, quantified 21% offender age sparsity, identified and handled the 1% of records with null labels (excluded from training, retained for inference), and verified train/test stratification (75/25 split over 110,928 incidents).

- **Designed a human-in-the-loop validation workflow** with WADOC stakeholders, defining a two-phase deployment process: Phase 1 — expert review of model predictions on held-out data; Phase 2 — label correction and model fine-tuning on corrected labels.

- **Architected a multi-tier modeling roadmap**: extended the incident-type classifier toward a hierarchical two-stage system (incident type → modifier prediction), using the covariance structure of incident type × modifier co-occurrences as a guiding production artifact.

- **Evaluated and documented NLP vectorization best practices**: benchmarked default TF-IDF vocabulary against filtered configurations with English stop words, domain-specific stop words (`incident`, `report`, `officer`, `staff`, `offender`), `max_df=0.95`, `min_df=5`, and bigram features — with word clouds, token frequency histograms, and TF-IDF heatmaps generated via matplotlib and seaborn.

- **Integrated cloud-backed data loading** using `google-cloud-storage` (GCS bucket `wadoc_smart_supervision`), enabling reproducible cloud-native training runs switchable via a `USE_CLOUD_STORAGE` flag with no code changes.

- **Communicated results and methodology to non-technical government stakeholders** through slide decks and written reports, explaining TF-IDF and multi-label classification in plain language, presenting confusion-matrix-style performance breakdowns per incident type, and advising on responsible deployment with human oversight.

---

## Cover Letter Paragraphs

### For AI / ML Engineer roles

> At WADOC, I led the development of an automated incident classification system for the Washington Department of Corrections. I built a complete machine learning pipeline in Python — using pandas for multi-table data ingestion and feature engineering, and scikit-learn for NLP vectorization and multi-label classification. The system ingests raw free-text narrative reports from a 24-table relational incident management system, constructs TF-IDF features (15K vocabulary, unigrams + bigrams), and trains a one-vs-rest logistic regression classifier across 73 binary incident type labels. The production model achieves 75.6% micro-F1 and 88.3% precision on 28K held-out incidents — a 30× improvement over a random baseline. Beyond modeling, I designed a human-in-the-loop validation workflow with agency stakeholders, performed systematic model diagnostics (feature weight analysis, per-label performance breakdowns), and architected a roadmap toward hierarchical two-stage modeling for modifier prediction.

### For Data Scientist roles

> In my work at WADOC, I applied end-to-end data science to a high-stakes public safety domain: building a system that automatically reads and classifies correctional incident reports for the Washington Department of Corrections. Starting from a 110,928-record dataset derived from a 24-table Oracle system, I designed the feature engineering pipeline using pandas (multi-block text concatenation, participant-level feature aggregation, one-hot label construction) and trained a multi-label classifier using scikit-learn (TF-IDF + Logistic Regression, one-vs-rest, 73 labels). The model achieves 75.6% F1 and 88.3% precision and was validated against multiple baselines including an age-only model and an all-negative classifier. I conducted detailed data quality audits, feature weight diagnostics, and NLP preprocessing analysis. I also translated findings for non-technical government stakeholders through clear documentation and slide presentations, and collaborated on defining a responsible human-in-the-loop deployment strategy.

---

## Key Technical Skills Demonstrated

| Category | Specifics |
|---|---|
| **ML / Modeling** | Multi-label classification, one-vs-rest strategy, logistic regression, random forests, hyperparameter tuning (L1/L2 regularization, penalty lambda) |
| **NLP** | TF-IDF vectorization (`TfidfVectorizer`), n-gram features, stop word engineering, sublinear TF scaling, vocabulary filtering (`max_df`, `min_df`) |
| **Feature Engineering** | Multi-table join/aggregation pipelines (`groupby`, `agg`, `merge`), one-hot encoding (`get_dummies`), multi-row narrative consolidation |
| **Evaluation** | Exact match accuracy, Jaccard score (micro), micro-F1, precision, recall, class-imbalance-aware baseline comparison, threshold selection |
| **Data Quality** | Missingness auditing, duplicate detection, label completeness validation, trainability assessment |
| **Data Engineering** | 24-table relational → 9 flat-file pipeline, GCS-backed cloud data loading, reproducible train/test splits |
| **Libraries** | pandas, numpy, scikit-learn, matplotlib, seaborn, google-cloud-storage |
| **Communication** | Stakeholder presentations, technical documentation, human-in-the-loop workflow design, per-label performance reporting |

---

## Performance Summary

| Metric | Value |
|---|---|
| Exact match accuracy | 60.6% |
| Jaccard score (micro) | 60.8% |
| F1 score (micro) | 75.6% |
| Precision | 88.3% |
| Recall | 66.1% |
| vs. random baseline | ~30× better |
| Training set size | ~83,200 incidents |
| Test set size | ~27,700 incidents |
| Number of labels | 73 incident types |
| Vocabulary size | 15,000 TF-IDF features |

---

## One-Line Summary

> Built a production multi-label NLP classifier at WADOC (pandas + scikit-learn) that automatically labels correctional incident reports across 73 categories with 75.6% F1 and 88.3% precision over 111K records — eliminating manual review work for Washington DOC staff.
