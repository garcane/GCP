# GOOGLE CLOUD CHILD PROJECT PROMPT
# Retail Analytics, Forecasting & Customer Intelligence Platform

You are operating under the previously defined:

"CLOUD PORTFOLIO — MASTER AGENT PROMPT"

That master prompt is the governing constitution for this project.

You MUST inherit and obey all principles, standards, agentic loops, evidence requirements, security requirements, cost controls, documentation requirements, testing requirements, and definition-of-done criteria from the Master Agent Prompt.

This document adds Google Cloud-specific requirements and project context.

======================================================================
PROJECT IDENTITY
======================================================================

Project name:

Google Cloud — Retail Analytics, Forecasting & Customer Intelligence Platform

Cloud:

Google Cloud Platform (GCP)

Primary sector:

Retail / E-commerce

Dataset:

Olist Brazilian E-Commerce Public Dataset

Primary technologies:

- Google Cloud Storage
- BigQuery
- Dataflow
- Vertex AI
- Vertex AI Model Registry
- Cloud Monitoring
- Cloud IAM
- Secret Manager where required
- Python
- SQL
- Pandas / Polars where appropriate
- scikit-learn
- XGBoost where appropriate
- TensorFlow only where genuinely justified
- Jupyter
- Git / GitHub
- Power BI or another suitable BI layer where practical

The project MUST NOT become a generic "GCP tutorial."

It must demonstrate the ability to design, build, operate, evaluate, and explain a realistic analytical and machine-learning platform on Google Cloud.

======================================================================
1. PROJECT PURPOSE
======================================================================

Build an end-to-end retail analytics and machine-learning platform using the Olist Brazilian E-Commerce Public Dataset.

The platform should demonstrate the progression:

LOCAL DATA SCIENCE
        ↓
CLOUD OBJECT STORAGE
        ↓
DATA ENGINEERING
        ↓
ANALYTICAL WAREHOUSING
        ↓
BUSINESS INTELLIGENCE
        ↓
MACHINE LEARNING
        ↓
MODEL REGISTRY
        ↓
MODEL DEPLOYMENT / INFERENCE
        ↓
MONITORING
        ↓
DOCUMENTATION / GOVERNANCE

The project must demonstrate genuine use of Google Cloud rather than simply uploading an existing notebook to Vertex AI.

The core GCP differentiator should be:

"Cloud-native analytical warehousing + scalable data processing + machine learning."

BigQuery should be treated as a central analytical component rather than merely an intermediate storage location.

======================================================================
2. DATASET
======================================================================

Use:

Olist Brazilian E-Commerce Public Dataset

The dataset contains approximately 100,000 orders from a Brazilian e-commerce marketplace and includes multiple related tables covering areas such as:

- customers
- orders
- order items
- payments
- reviews
- products
- sellers
- product categories
- geolocation

The dataset is particularly valuable because it is relational rather than a single flat CSV.

This project MUST exploit that relational structure.

Do not flatten everything immediately into one massive dataframe.

First understand:

- table relationships
- primary keys
- foreign keys
- cardinality
- grain
- duplicate relationships
- temporal fields
- missing values
- referential integrity
- business meaning
- potential leakage
- unusual records
- date ranges
- currency / monetary fields
- delivery timestamps
- review timestamps
- customer identifiers
- seller identifiers
- product identifiers

Verify the dataset's current source, licence, attribution requirements, and permitted portfolio usage during Phase 0.

Do not assume licensing information from memory.

======================================================================
3. BUSINESS SCENARIO
======================================================================

Assume the project represents a hypothetical e-commerce analytics function.

The business wants to understand:

1. How sales performance changes over time.
2. Which products and categories drive revenue.
3. Which sellers perform well or poorly.
4. How delivery performance affects customer satisfaction.
5. Which customers represent valuable segments.
6. What future demand may look like.
7. Which orders/customers/products may present elevated operational or commercial risk.
8. How customer behaviour can be converted into actionable analytical features.
9. How the resulting analytical and ML workloads can operate reliably in the cloud.

This is an educational portfolio project.

Do not present Olist-derived models as production-ready recommendations for a real company.

Do not make unsupported causal claims.

For example:

"Late delivery causes poor reviews"

must NOT be stated simply because the data shows an association.

Instead use language such as:

"Late delivery is associated with lower review scores in this dataset."

======================================================================
4. CORE ANALYTICAL QUESTIONS
======================================================================

The project should answer meaningful business questions.

At minimum investigate:

### Sales

- What is total revenue over time?
- What are the strongest product categories?
- Which sellers generate the most revenue?
- What is average order value?
- How does order volume change over time?
- What are the major revenue trends?

### Customer

- How many unique customers are present?
- How frequently do customers purchase?
- What does customer value look like?
- Can customers be segmented using behavioural characteristics?
- What distinguishes higher-value customers from lower-value customers?

### Delivery

- How long do orders take to fulfil?
- Which sellers/categories have poor delivery performance?
- How frequently are orders delivered late?
- Is delivery performance associated with review scores?

### Reviews

- What drives higher/lower review scores?
- How are review scores distributed?
- Is there an observable relationship between delivery performance and customer satisfaction?

### Forecasting

- How does order/revenue demand evolve over time?
- Can future order volume or revenue be forecast?
- How accurately can a baseline model forecast demand?

### Machine Learning

- Can customers be segmented?
- Can customer/order behaviour be used to predict a meaningful business outcome?
- Can future customer behaviour be estimated from historical information?

The exact final ML problem MUST be selected after exploratory analysis.

Do not force an arbitrary ML problem merely to include machine learning.

======================================================================
5. GCP ARCHITECTURE
======================================================================

Preferred conceptual architecture:

LOCAL DEVELOPMENT
        ↓
LOCAL EDA / BASELINE
        ↓
GOOGLE CLOUD STORAGE
        ↓
DATAFLOW
        ↓
BIGQUERY
        ↓
ANALYTICAL / DIMENSIONAL MODEL
        ↓
BI / SQL ANALYTICS
        ↓
FEATURE ENGINEERING
        ↓
VERTEX AI
        ↓
MODEL REGISTRY
        ↓
BATCH OR CONTROLLED ONLINE INFERENCE
        ↓
CLOUD MONITORING
        ↓
DOCUMENTATION / EVIDENCE

The final architecture MUST be justified.

Do not automatically deploy every possible GCP service.

======================================================================
6. GOOGLE CLOUD SERVICES
======================================================================

Investigate current Google Cloud services, capabilities, quotas, pricing, and free-tier/credit implications before provisioning.

Potential services include:

### Google Cloud Storage

Use for:

- raw source data
- immutable source files
- staging artefacts
- processed files where appropriate
- model artefacts
- exported predictions
- project evidence where appropriate

Use logical storage layers such as:

gs://project-bucket/raw/
gs://project-bucket/staging/
gs://project-bucket/curated/
gs://project-bucket/features/
gs://project-bucket/models/
gs://project-bucket/predictions/

Exact bucket structure must be decided during architecture.

### BigQuery

BigQuery should be the analytical centre of the project.

Use it for:

- structured analytical data
- SQL transformations
- dimensional modelling
- aggregation
- feature preparation
- business metrics
- exploratory analytical queries
- analytical datasets
- ML-ready datasets where appropriate

Demonstrate:

- partitioning
- clustering
- appropriate data types
- efficient SQL
- query-cost awareness
- schema design
- analytical grain
- reusable views / tables
- data quality checks

Do NOT treat BigQuery as merely "a place to put CSV files."

### Dataflow

Use Dataflow where it provides genuine value.

Potential responsibilities:

- ingestion
- transformation
- schema normalisation
- multi-table processing
- scalable ETL
- conversion to analytics-ready formats

However:

Do not use Dataflow merely because it is a Google Cloud service.

For small datasets, compare:

- local transformation
- BigQuery SQL
- Dataflow

and justify the selected approach.

If Dataflow is used, demonstrate that you understand:

- pipeline stages
- transforms
- workers
- execution
- failure handling
- scalability
- cost implications

### Vertex AI

Use Vertex AI for the machine-learning lifecycle.

Potential responsibilities:

- training
- experiment tracking
- model artefacts
- model evaluation
- model registry
- model deployment
- batch prediction
- controlled online prediction

Vertex AI must represent a genuine ML lifecycle rather than simply hosting a notebook.

### Vertex AI Model Registry

Register the champion model.

Record:

- model name
- version
- training dataset
- feature version
- training timestamp
- model type
- evaluation metrics
- hyperparameters
- artefact location
- dependencies
- limitations
- approval status

### Cloud Monitoring

Use Cloud Monitoring for relevant operational visibility.

Potential monitoring areas:

- pipeline execution
- inference activity
- resource utilisation
- errors
- latency where applicable
- scheduled workload health

ML/data drift may be demonstrated if practical.

If simulated data is used to demonstrate drift, explicitly label it as simulated.

### Cloud IAM

Implement least-privilege access.

Consider:

- service accounts
- human developer access
- storage permissions
- BigQuery permissions
- Vertex AI permissions

Do not use broad Owner/Editor permissions simply for convenience unless absolutely unavoidable during initial setup.

Document why each role exists.

### Secret Manager

Use Secret Manager only when secrets genuinely exist.

Never hard-code:

- API keys
- credentials
- service account secrets
- passwords
- tokens

into source code or Git history.

======================================================================
7. LOCAL-FIRST DEVELOPMENT
======================================================================

Local development should remain an important component.

Do not move every experiment into GCP.

Use local resources for:

- initial EDA
- data understanding
- feature experimentation
- baseline models
- model comparison
- rapid iteration
- debugging
- visualisation

Suggested notebooks:

notebooks/
    01_dataset_discovery.ipynb
    02_local_eda.ipynb
    03_data_quality.ipynb
    04_customer_analytics.ipynb
    05_forecasting_baseline.ipynb
    06_ml_baseline.ipynb
    07_model_evaluation.ipynb
    08_threshold_or_segmentation_analysis.ipynb

Do not allow notebooks to become the production implementation.

Reusable logic belongs in:

src/

SQL belongs in:

sql/

Configuration belongs in:

config/

Infrastructure belongs in:

infrastructure/

======================================================================
8. DATA ENGINEERING LAYERS
======================================================================

Implement a clear data lifecycle.

Recommended conceptual layers:

RAW
↓
STAGING
↓
CURATED
↓
ANALYTICAL
↓
FEATURES
↓
PREDICTIONS

Each layer must have a documented purpose.

### RAW

Original source data.

Requirements:

- preserve source fidelity
- avoid destructive transformations
- document source
- record ingestion timestamp where appropriate

### STAGING

Standardisation layer.

Potential operations:

- column naming
- data type conversion
- date parsing
- null handling
- duplicate detection
- schema validation

### CURATED

Clean relational data.

Requirements:

- validated relationships
- consistent schemas
- business-friendly naming
- quality checks

### ANALYTICAL

BigQuery analytical layer.

Potential modelling approach:

FACT + DIMENSION architecture.

For example:

FactOrders
FactOrderItems
FactPayments
FactReviews

Dimensions might include:

DimCustomer
DimProduct
DimSeller
DimDate
DimGeography

The exact schema must be determined after inspecting the dataset.

Do not create dimensions merely to satisfy a textbook definition.

======================================================================
9. DATA MODELLING
======================================================================

Data grain MUST be explicitly documented.

For every major table state:

- table name
- grain
- primary key
- foreign keys
- measures
- dimensions
- source tables
- transformation logic

Example:

FactOrderItems

Grain:

One row per order item.

Potential measures:

- price
- freight value
- item count

Potential dimensions:

- customer
- seller
- product
- date
- order

The actual implementation must be validated against the source relationships.

Avoid accidental many-to-many joins.

Demonstrate that joining order-level, item-level, payment-level, and review-level tables can multiply records if performed incorrectly.

This is an important data-engineering competency.

======================================================================
10. BIGQUERY ENGINEERING
======================================================================

BigQuery should demonstrate real analytical engineering.

Investigate and implement where beneficial:

### Partitioning

Potential candidates:

- order purchase date
- delivery date
- review creation date

Do not partition tables arbitrarily.

Explain why a particular partition column was chosen.

### Clustering

Potential clustering columns may include:

- customer_id
- seller_id
- product_id
- product_category

Select based on query patterns rather than arbitrary preference.

### Query optimisation

Demonstrate awareness of:

- SELECT *
- unnecessary scans
- repeated transformations
- partition pruning
- clustering
- aggregation strategy
- materialised analytical tables where justified

Track query size/cost implications.

### Reusable SQL

Create modular SQL rather than putting all transformations into one giant query.

Potential structure:

sql/
    staging/
    curated/
    dimensions/
    facts/
    analytics/
    features/

======================================================================
11. DATA QUALITY
======================================================================

Build automated data-quality checks.

At minimum test:

- row counts
- null rates
- duplicate primary keys
- referential integrity
- date validity
- numerical ranges
- impossible values
- orphan records
- unexpected categories
- join multiplication
- schema consistency

Potential examples:

- every order item references a valid order
- every order references a customer
- prices are non-negative
- timestamps follow logical ordering
- review scores are within expected range

Data-quality results should be documented.

If quality issues are found in the original dataset, do not silently remove them.

Record:

- issue
- frequency
- treatment
- rationale
- impact

======================================================================
12. CUSTOMER ANALYTICS
======================================================================

Develop meaningful customer-level features.

Potential features:

- order count
- total spend
- average order value
- recency
- purchase frequency
- category diversity
- average review score
- delivery experience
- geographic characteristics

Consider an RFM-style framework:

Recency
Frequency
Monetary Value

But do not blindly copy a textbook RFM implementation.

Explain:

- feature definitions
- observation period
- cutoff date
- leakage risks
- customer grain

Potential customer segments:

- high-value frequent customers
- high-value infrequent customers
- recent customers
- dormant customers
- low-engagement customers

Use neutral descriptive language rather than unsupported claims about customer behaviour.

======================================================================
13. CUSTOMER SEGMENTATION
======================================================================

Evaluate whether unsupervised learning provides value.

Potential models:

- K-Means
- hierarchical clustering
- Gaussian mixture models if justified

Potential features:

- spend
- order frequency
- recency
- average basket/order value
- category diversity

Evaluate:

- silhouette score
- cluster size
- stability
- business interpretability

Do not select a cluster count purely because an algorithm produces one.

Explain why the final segmentation is useful.

If segmentation adds little value, document that finding and do not force it into the final architecture.

======================================================================
14. FORECASTING
======================================================================

Build at least one meaningful forecasting experiment.

Potential targets:

- daily order volume
- weekly order volume
- daily revenue
- weekly revenue

Start with a simple baseline.

Examples:

- naïve forecast
- seasonal naïve forecast
- moving average

Then compare with an appropriate model.

Potential models:

- linear regression with time features
- tree-based regression
- exponential smoothing
- ARIMA-style methods if justified
- other appropriate forecasting methods

Do not use deep learning merely because TensorFlow is available.

Evaluate using appropriate metrics such as:

- MAE
- RMSE
- MAPE where appropriate
- sMAPE where appropriate

Use time-aware train/validation/test splits.

Never randomly shuffle temporal observations for forecasting evaluation.

Document:

- forecast horizon
- training period
- validation period
- test period
- seasonality assumptions
- limitations

======================================================================
15. SUPERVISED MACHINE LEARNING
======================================================================

Select a supervised ML problem only after EDA.

Potential problems could include:

- predicting review-score category
- predicting delivery-related outcomes
- predicting customer repeat behaviour
- predicting customer value category

The target must have:

- a clear definition
- a clear prediction unit
- a clear prediction horizon
- sufficient observations
- meaningful business interpretation

Do not use future information to predict past outcomes.

Explicitly investigate:

- target leakage
- temporal leakage
- post-outcome variables
- duplicated information
- identifiers
- high-cardinality features
- target-derived features

Create:

docs/ml/LEAKAGE_ANALYSIS.md

======================================================================
16. MODEL COMPARISON
======================================================================

At minimum compare appropriate baseline models.

For a classification task:

- Logistic Regression
- Random Forest
- XGBoost

For regression:

- Linear Regression
- Random Forest Regressor
- XGBoost Regressor

The exact models may change depending on the selected problem.

Do not compare models merely for quantity.

Explain:

- baseline
- model assumptions
- strengths
- weaknesses
- computational requirements
- interpretability
- performance
- operational suitability

======================================================================
17. MODEL EVALUATION
======================================================================

Accuracy alone MUST NOT be treated as sufficient.

For classification investigate:

- Accuracy
- Precision
- Recall
- F1
- ROC-AUC
- PR-AUC
- confusion matrix
- calibration
- threshold analysis

For regression investigate:

- MAE
- RMSE
- R²
- residual behaviour

For forecasting investigate appropriate temporal metrics.

The final model should not automatically be the model with the highest single metric.

Consider:

PERFORMANCE
+
INTERPRETABILITY
+
CALIBRATION
+
COMPUTATIONAL COST
+
OPERATIONAL COMPLEXITY
+
BUSINESS VALUE

======================================================================
18. THRESHOLD ANALYSIS
======================================================================

If classification is used, do not assume a 0.5 classification threshold.

Evaluate different thresholds.

Demonstrate how threshold selection changes:

- precision
- recall
- intervention volume
- false positives
- false negatives

If a business cost matrix is used:

- explicitly label it hypothetical
- explain assumptions
- do not present it as real Olist business economics

======================================================================
19. EXPLAINABILITY
======================================================================

Use appropriate explainability methods.

Potential methods:

- feature importance
- permutation importance
- SHAP

Explain:

"Predictive importance is not the same as causality."

Where possible distinguish:

- global importance
- local explanations
- model behaviour
- business interpretation

Do not overclaim.

======================================================================
20. VERTEX AI
======================================================================

The final model must have a reproducible cloud implementation.

The cloud workflow should demonstrate:

1. Training data preparation.
2. Training configuration.
3. Model training.
4. Evaluation.
5. Model artefact creation.
6. Model registration.
7. Candidate model evaluation.
8. Approval decision.
9. Inference.
10. Monitoring.

Do not simply upload a notebook and call this MLOps.

Reusable training code should exist outside the notebook.

Potential structure:

src/ml/
    train.py
    evaluate.py
    predict.py
    features.py
    preprocessing.py

======================================================================
21. CLOUD TRAINING VS LOCAL TRAINING
======================================================================

The project should explicitly distinguish:

LOCAL EXPERIMENTATION

from

CLOUD REPRODUCTION / PRODUCTION-LIKE TRAINING

Use local compute for rapid experimentation.

Once the champion approach is selected:

reproduce the final training workflow in Vertex AI where technically and economically justified.

Document:

- local environment
- cloud environment
- dependencies
- dataset version
- feature version
- random seed
- model configuration
- evaluation metrics

The goal is reproducibility.

======================================================================
22. MODEL REGISTRY
======================================================================

The champion model should be registered.

The registry entry/documentation should identify:

- model name
- model version
- training dataset
- feature set
- training code version
- Git commit
- model type
- evaluation metrics
- model artefact
- dependency environment
- limitations
- approval status

Use a lifecycle such as:

EXPERIMENT
    ↓
CANDIDATE
    ↓
VALIDATED
    ↓
APPROVED
    ↓
DEPLOYED

Do not deploy models automatically without evaluation.

======================================================================
23. BATCH VS ONLINE INFERENCE
======================================================================

Explicitly compare:

### Batch inference

Advantages:

- lower operational complexity
- potentially lower cost
- appropriate for scheduled customer analytics
- no always-on endpoint

### Online inference

Advantages:

- low-latency predictions
- suitable for interactive applications

Disadvantages:

- endpoint costs
- operational complexity
- monitoring requirements
- security considerations

For this portfolio project, batch inference should generally be preferred unless the selected business problem genuinely requires real-time predictions.

If an online endpoint is created:

- keep it temporary
- test it
- capture evidence
- document the cost
- delete it when no longer required

======================================================================
24. MONITORING
======================================================================

Implement appropriate monitoring.

Operational monitoring may include:

- pipeline failures
- job status
- inference activity
- latency
- errors
- resource utilisation

For ML monitoring, investigate where practical:

- prediction distribution
- feature distribution
- data drift
- performance degradation
- input schema changes

If no genuine production stream exists, create a controlled demonstration.

Any simulated future data MUST be explicitly labelled as simulated.

Do not pretend that synthetic monitoring data represents real production drift.

======================================================================
25. SECURITY
======================================================================

Apply least privilege.

Document:

- IAM structure
- service accounts
- bucket permissions
- BigQuery permissions
- Vertex AI permissions
- secrets management
- encryption
- network considerations where applicable

Do not commit:

- service-account JSON files
- credentials
- API keys
- passwords
- tokens

Add appropriate patterns to:

.gitignore

and verify that no secrets exist in Git history.

======================================================================
26. COST OPTIMISATION
======================================================================

Cost is a first-class engineering constraint.

The Olist dataset is not large enough to justify pretending this requires enormous infrastructure.

Before provisioning:

research current GCP pricing.

Pay particular attention to:

- BigQuery bytes processed
- BigQuery storage
- Dataflow worker time
- Vertex AI training compute
- Vertex AI endpoints
- Cloud Storage
- monitoring/logging

Avoid unnecessary always-on infrastructure.

Avoid:

- oversized Dataflow workers
- excessive BigQuery scans
- unnecessary duplicate datasets
- permanent Vertex AI endpoints
- unnecessarily complex orchestration

Demonstrate practical cost optimisation.

Potential experiment:

"Unoptimised BigQuery query vs partition-aware / clustered query"

or:

"Local training vs Vertex AI training"

or:

"Batch inference vs online endpoint"

Document:

- what was tested
- resource used
- approximate cost implication
- performance difference
- engineering conclusion

======================================================================
27. DATA PRIVACY & RESPONSIBLE ANALYTICS
======================================================================

Although this is a public dataset, treat data responsibly.

Document:

- dataset provenance
- licence
- limitations
- privacy considerations
- sensitive or quasi-identifying fields
- geographic information
- customer identifiers

Do not imply that the dataset represents all Brazilian e-commerce customers.

Do not generalise findings beyond the dataset without evidence.

For customer segmentation and ML, consider:

- proxy variables
- geographic bias
- historical bias
- representativeness
- transparency
- human oversight

======================================================================
28. POWER BI / BUSINESS INTELLIGENCE
======================================================================

Where practical, expose BigQuery analytical outputs to Power BI.

The BI layer should focus on business consumption rather than simply reproducing SQL.

Potential report sections:

### Executive Overview

- revenue
- orders
- customers
- AOV
- growth
- delivery performance

### Product Performance

- category revenue
- order volume
- product performance

### Seller Performance

- revenue
- orders
- delivery performance
- review performance

### Customer Intelligence

- customer segments
- RFM
- repeat behaviour
- customer value

### Forecasting

- historical demand
- forecast
- confidence intervals where available

### ML

- model performance
- prediction distribution
- feature importance
- segment / risk distribution where appropriate

The BI model should be based on the analytical model rather than raw files wherever possible.

======================================================================
29. TESTING
======================================================================

Implement testing throughout the project.

Potential tests:

### Data tests

- schema
- nulls
- uniqueness
- referential integrity
- ranges

### Transformation tests

- expected row counts
- aggregation correctness
- join correctness
- grain validation

### ML tests

- feature schema
- target schema
- reproducibility
- prediction shape
- valid prediction ranges

### Pipeline tests

- successful execution
- failure handling
- expected outputs

### Infrastructure tests

- resources exist
- correct permissions
- expected configuration

Tests must be automated where practical.

======================================================================
30. EVIDENCE REQUIREMENTS
======================================================================

Evidence must come from the real Google Cloud environment.

Do NOT fabricate screenshots.

Capture meaningful checkpoints.

Suggested evidence checkpoints:

E01 — GCP project / billing configuration
E02 — IAM / service accounts
E03 — Cloud Storage bucket
E04 — Raw dataset uploaded
E05 — Dataflow pipeline
E06 — Dataflow execution
E07 — BigQuery datasets
E08 — BigQuery analytical tables
E09 — Partitioning / clustering
E10 — Data-quality results
E11 — Analytical queries
E12 — Local model baseline
E13 — Vertex AI training job
E14 — Model evaluation
E15 — Vertex AI Model Registry
E16 — Batch inference
E17 — Online endpoint if used
E18 — Monitoring
E19 — Cost analysis
E20 — Resource cleanup

Do not screenshot every action.

Each evidence item should demonstrate a meaningful capability.

Store evidence references in:

docs/evidence/

and track them in:

PROJECT_STATUS.md

======================================================================
31. FAILURE DOCUMENTATION
======================================================================

Failures are evidence of engineering experience.

If something breaks, document:

- what was attempted
- expected behaviour
- actual behaviour
- error
- diagnosis
- attempted fixes
- final solution
- lesson learned

Potential examples:

- Dataflow schema mismatch
- BigQuery join multiplication
- partitioning mistake
- IAM permission error
- Vertex AI dependency issue
- model deployment failure
- cost unexpectedly higher than expected
- invalid feature schema

Do not hide meaningful failures.

======================================================================
32. REPOSITORY STRUCTURE
======================================================================

Use a professional repository structure similar to:

README.md
ARCHITECTURE.md
DECISIONS.md
PROJECT_STATUS.md
COST.md
SECURITY.md
RESPONSIBLE_AI.md
MODEL_CARD.md
LICENSE
.gitignore

notebooks/
    01_dataset_discovery.ipynb
    02_local_eda.ipynb
    03_data_quality.ipynb
    04_customer_analytics.ipynb
    05_forecasting_baseline.ipynb
    06_ml_baseline.ipynb
    07_model_evaluation.ipynb
    08_model_interpretation.ipynb

src/
    ingestion/
    transformation/
    features/
    analytics/
    ml/
    monitoring/

sql/
    staging/
    curated/
    dimensions/
    facts/
    analytics/
    features/

tests/

infrastructure/

pipelines/

config/

docs/
    architecture/
    data/
    ml/
    evidence/
    decisions/
    failures/

models/

scripts/

The exact structure may evolve.

Do not create empty directories simply to make the repository look impressive.

======================================================================
33. DOCUMENTATION
======================================================================

README.md should tell the complete story:

1. Business problem
2. Dataset
3. Architecture
4. Why GCP
5. Data engineering
6. BigQuery analytical model
7. Analytics
8. Forecasting
9. Machine learning
10. Vertex AI
11. Model registry
12. Deployment
13. Monitoring
14. Security
15. Cost optimisation
16. Results
17. Limitations
18. Evidence
19. Reproduction instructions

ARCHITECTURE.md should explain:

- components
- data flow
- service responsibilities
- security boundaries
- failure points
- scalability
- cost considerations

DECISIONS.md should document important decisions using:

Decision
Context
Options
Chosen option
Reason
Trade-offs
Cost implications
Security implications
Alternatives rejected

======================================================================
34. PROJECT STATUS
======================================================================

Maintain:

PROJECT_STATUS.md

It MUST track:

Current phase:
Completed:
In progress:
Blocked:
Next:
Tests:
Evidence:
Cloud resources:
Estimated cost:
Security status:
Open decisions:
Known limitations:

Update it after meaningful milestones.

======================================================================
35. AGENTIC EXECUTION LOOP
======================================================================

For every significant task use:

PLAN
↓
INSPECT
↓
IMPLEMENT
↓
TEST
↓
VERIFY
↓
EVIDENCE
↓
DOCUMENT
↓
REVIEW
↓
STATUS
↓
DECIDE

Never skip VERIFY.

Never claim success merely because a command returned successfully.

Verification must confirm the intended outcome.

Example:

Do not say:

"Dataflow job submitted successfully."

Instead verify:

- job completed
- expected output exists
- row counts are correct
- schema is correct
- data quality checks pass
- BigQuery can consume the result

======================================================================
36. HUMAN APPROVAL GATES
======================================================================

Pause and request approval before:

- major architecture changes
- unexpectedly expensive resources
- permanent or always-on services
- production-like online endpoints
- security-sensitive configuration
- deleting important cloud resources
- changing the core ML objective
- changing the dataset
- introducing unnecessary services
- accepting significant technical debt

Do not pause for trivial implementation details.

======================================================================
37. GCP-SPECIFIC LEARNING OBJECTIVES
======================================================================

By completion, the repository should demonstrate that the user understands:

### Google Cloud fundamentals

- projects
- billing
- IAM
- service accounts
- regions
- resource hierarchy

### Cloud Storage

- buckets
- object organisation
- lifecycle considerations
- permissions

### Dataflow

- distributed processing
- pipeline design
- transformations
- workers
- execution
- cost

### BigQuery

- analytical warehousing
- SQL
- schemas
- partitioning
- clustering
- optimisation
- dimensional modelling
- query economics

### Vertex AI

- training
- model artefacts
- model evaluation
- model registry
- deployment
- batch prediction
- monitoring

### MLOps

- reproducibility
- versioning
- model lifecycle
- deployment
- monitoring

### Data Engineering

- ingestion
- transformation
- quality
- orchestration
- lineage
- analytical modelling

### Analytics Engineering

- dimensional modelling
- reusable SQL
- business metrics
- semantic consistency

======================================================================
38. CROSS-CLOUD DIFFERENTIATION
======================================================================

This project MUST NOT simply replicate the Azure or AWS project.

The three portfolio projects should demonstrate different architectural strengths.

Azure:

Healthcare
+
Data Factory / Databricks
+
Azure ML
+
Healthcare predictive analytics

AWS:

Financial Services
+
S3 / Glue / Athena
+
SageMaker
+
Credit risk / classification

GCP:

Retail / E-commerce
+
Cloud Storage / Dataflow / BigQuery
+
Vertex AI
+
Customer intelligence / forecasting / analytical warehousing

GCP should therefore place particularly strong emphasis on:

BIGQUERY
+
SQL ANALYTICS
+
DIMENSIONAL MODELLING
+
DATAFLOW
+
CUSTOMER INTELLIGENCE
+
FORECASTING
+
VERTEX AI

Do not weaken this differentiation by making all three architectures identical.

======================================================================
39. COST-CONSCIOUS ARCHITECTURE
======================================================================

The project must optimise for:

MAXIMUM DEMONSTRATED COMPETENCY
per
UNIT OF CLOUD COMPLEXITY
per
UNIT OF CLOUD COST

Before creating a resource ask:

1. What competency does this demonstrate?
2. Is this the simplest service that demonstrates it?
3. What does it cost?
4. Can it be temporary?
5. Can the workload run locally?
6. Can a serverless service replace an always-on resource?
7. Is the complexity justified?
8. Does the service materially improve the portfolio?

If the answer to these questions is weak, do not provision the service.

======================================================================
40. FINAL PROJECT AUDIT
======================================================================

Before declaring the project complete, conduct a full audit.

Verify:

DATA
- dataset provenance documented
- licence documented
- schemas understood
- relationships validated
- data quality tested
- leakage investigated

GCP
- IAM reviewed
- storage reviewed
- Dataflow reviewed
- BigQuery reviewed
- Vertex AI reviewed
- monitoring reviewed
- unnecessary resources removed

DATA ENGINEERING
- raw/staging/curated layers implemented
- transformations reproducible
- analytical model documented
- BigQuery optimisation demonstrated

ANALYTICS
- business questions answered
- metrics validated
- BI output usable

ML
- target justified
- leakage investigated
- baseline established
- models compared
- metrics appropriate
- explainability included
- limitations documented

MLOPS
- cloud training reproducible
- model registered
- inference demonstrated
- monitoring implemented

SECURITY
- least privilege
- no secrets committed
- credentials protected

COST
- major cost drivers identified
- optimisation demonstrated
- temporary resources removed

DOCUMENTATION
- README complete
- architecture documented
- decisions documented
- model card complete
- responsible AI documented
- evidence captured
- failures documented
- PROJECT_STATUS.md current

REPRODUCIBILITY
- setup instructions tested
- dependencies documented
- commands work
- repository is clean

======================================================================
41. DEFINITION OF DONE
======================================================================

The project is NOT complete when:

"the model works."

The project is complete only when:

IMPLEMENTATION
+
TESTING
+
VERIFICATION
+
CLOUD DEPLOYMENT
+
DATA ENGINEERING
+
ANALYTICS
+
MACHINE LEARNING
+
MLOPS
+
SECURITY
+
COST OPTIMISATION
+
EVIDENCE
+
DOCUMENTATION
+
REPRODUCIBILITY

are all sufficiently demonstrated.

The final repository should allow a technical interviewer to answer:

"Can this person actually build something on GCP?"

with:

"Yes."

======================================================================
42. INTERVIEW STANDARD
======================================================================

Every major architecture decision should be explainable in an interview.

The user should be able to answer:

Why GCP?

Why Cloud Storage?

Why Dataflow?

Why BigQuery?

Why this BigQuery schema?

Why partitioning?

Why clustering?

Why not process everything locally?

Why not use a traditional database?

Why Vertex AI?

Why this model?

Why not another model?

How did you prevent leakage?

Why this evaluation metric?

Why batch instead of real-time?

How would this scale?

What would break first?

How would you secure it?

How much does it cost?

What would you change for production?

What are the limitations of the dataset?

If an answer cannot be explained clearly, the implementation should be reconsidered or documented better.

======================================================================
43. STARTING INSTRUCTION
======================================================================

DO NOT immediately provision the complete GCP architecture.

Begin with PHASE 0 — DISCOVERY.

First inspect and establish:

1. Dataset source.
2. Dataset licence.
3. Dataset structure.
4. Table relationships.
5. Data types.
6. Date ranges.
7. Missing values.
8. Duplicate records.
9. Referential integrity.
10. Potential analytical grains.
11. Candidate business questions.
12. Candidate forecasting target.
13. Candidate ML target.
14. Leakage risks.
15. Customer-level feature opportunities.
16. Current Google Cloud services relevant to the architecture.
17. Current GCP pricing.
18. Free-tier / credit implications.
19. Required IAM configuration.
20. Minimal viable architecture.
21. Potential architectural alternatives.
22. Cost risks.
23. Evidence requirements.

Produce a Phase 0 discovery report before substantial infrastructure provisioning.

Do not blindly follow the proposed architecture if discovery shows that a simpler or better architecture is appropriate.

The objective is not:

"Use as many GCP services as possible."

The objective is:

"Demonstrate that the user can design and operate a credible, cost-conscious, analytical and machine-learning platform on Google Cloud."

======================================================================
END OF GOOGLE CLOUD CHILD PROJECT PROMPT
======================================================================
