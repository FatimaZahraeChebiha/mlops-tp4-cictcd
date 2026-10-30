# Sentiment Model

## Use case
Classification binaire de sentiment.

## Version
sentiment-model, version 1 (run MLflow : sentiment-candidate).

## Dataset
reviews.csv -- jeu pedagogique.

## Method
TF-IDF + Logistic Regression.

## Parameters
C = 1.0
max_features = 5000
ngram_range = [1, 2]

## Metrics
Accuracy = 0.4
F1 = 0.571

## Quality Gates
Unit tests = 3/3 passed
Data tests = 4/4 passed
Model tests = 1/2 passed (test_model_quality_gate failed : accuracy 0.4 < 0.60)
Security checks = Bandit : 0 issue ; pip-audit : 2 vulnerabilites (pytest 8.4.2)

## Known limitations
- Petit jeu de donnees pedagogique.
- Langue principalement francaise.
- Evaluation non representative d'un contexte industriel.

## Governance
validation_status = passed
approval_status = approved
alias = candidate / champion

## Deployment decision
Version REJETEE : la Quality Gate G3 (accuracy >= 0.60) et le controle de securite pip-audit echouent.
Dans GitHub Actions, le job quality echoue, donc les jobs staging et production ne sont pas executes.
Le tag validation_status = passed a ete pose automatiquement par train_and_register.py, sans tenir compte des tests.