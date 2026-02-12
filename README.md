# Credit Card Fraud Detection with Azure Machine Learning

This project implements a Machine Learning model to detect fraudulent credit card transactions using Azure Machine Learning AutoML.

## 📋 Project Description

The goal is to build and evaluate a classification model capable of distinguishing between legitimate and fraudulent transactions in an imbalanced credit card transaction dataset.

## 🚀 Initial Setup

### Prerequisites
- Active Azure account
- Azure Machine Learning Workspace
- Configured Compute Instance

### Setup Steps

1. **Create and Run Compute Instance**
   - Navigate to Compute in Azure ML Studio
   - Create new compute instance
   - Wait for status to be "Running"

2. **Configure Datastore**
   - Create a datastore in Azure Blob Storage
   - Upload the credit card fraud dataset

## 📊 Dataset

**Source**: [Credit Card Fraud Data on Kaggle](https://www.kaggle.com/datasets/chetanmittal033/credit-card-fraud-data)

### Features Used

The model uses the following columns from the dataset:

- `trans_date_trans_time` - Transaction date and time
- `category` - Merchant category
- `amt` - Transaction amount
- `gender` - Cardholder gender
- `city`, `state`, `zip` - Location
- `lat`, `long` - Geographic coordinates
- `city_pop` - City population
- `job` - Cardholder occupation
- `dob` - Date of birth
- `unix_time` - Unix timestamp
- `merch_lat`, `merch_long` - Merchant coordinates
- **`is_fraud`** - Target variable (0: legitimate, 1: fraud)

### Removed Features

To optimize the model, the following columns were removed:
- `trans_num` - Transaction number
- `street` - Street address
- `first`, `last` - Cardholder names
- `cc_num` - Credit card number
- `sn` - Serial number
- `merchant` - Merchant name

## 🛠️ Training Process

### 1. Create Automated ML Job

- Select **Train automatically**
- Configure job name and experiment
- Task type: **Classification**

### 2. Dataset Configuration

- Source: Azure Blob Storage
- Format: Delimited (CSV)
- Configure headers and delimiters
- Validate data schema

### 3. Model Configuration

- **Target variable**: `is_fraud`
- **Primary metric**: `AveragePrecisionScoreWeighted`
- **Validation**: Automatic
- Enable all supported models
- Configure positive class label

### 4. Compute Configuration

- Select previously created Compute Instance
- Configure timeout and resources as needed

## 📈 Model Results

The trained model achieved the following performance metrics:

| Metric | Value |
|---------|-------|
| **Accuracy** | 0.99916 |
| **AUC Weighted** | 0.99820 |
| **Average Precision Score Weighted** | 0.99976 |
| **F1 Score Weighted** | 0.99912 |
| **Precision Score Weighted** | 0.99914 |
| **Recall Score Weighted** | 0.99916 |
| **Balanced Accuracy** | 0.90675 |
| **Matthews Correlation** | 0.88474 |

### Training Details

- **Total duration**: 17m 28.31s
- **Status**: Completed ✅
- **Model name**: `epic_jicama_c2ldq2xxmm`

## 💡 Model Highlights

- Effective handling of imbalanced datasets
- High accuracy in fraud detection
- Low number of false positives
- Excellent balance between precision and recall

## 📝 Next Steps

1. **Deployment**: Deploy the model as a web service
2. **Monitoring**: Configure data drift monitoring
3. **Retraining**: Establish periodic retraining pipeline
4. **Optimization**: Perform hyperparameter tuning for additional improvements

## 🔧 Technologies Used

- Azure Machine Learning
- Azure Blob Storage
- Automated ML
- Python SDK (implicit in AutoML)
---

**Note**: This project uses Azure Machine Learning AutoML to automate the model selection and optimization process, facilitating the implementation of high-quality ML solutions.
