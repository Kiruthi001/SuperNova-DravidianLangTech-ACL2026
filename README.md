The SUPERNOVA system was developed for the shared task on Abusive Tamil Text Targeting Women on Social Media at DravidianLangTech@ACL 2026. We investigated three complementary modeling approaches to address abusive text detection in Tamil and code-mixed content.

First, we fine-tuned the MuRIL transformer model with class balancing and label smoothing. Second, we combined MuRIL sentence embeddings with an XGBoost classifier and applied threshold tuning for improved decision boundaries. Third, we designed a CPU-efficient ensemble model integrating character-level TF-IDF features and SentenceBERT embeddings with Random Forest and Extra Trees classifiers.

Our best submission achieved an accuracy of 0.8007 and a macro F1-score of 0.7994, securing 11th place among all participating teams. The repository contains implementation details, training configurations, and submission files for all three experimental runs.
