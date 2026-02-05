# Vehicle Insurance Prediction

Welcome to the **Vehicle Insurance Data Pipeline** project!  
This repository demonstrates a complete **MLOps pipeline** for managing, processing, and deploying machine learning models on vehicle insurance data.  

It highlights **end-to-end workflows**, including **data ingestion, validation, transformation, model training, evaluation, deployment, and CI/CD automation** using modern tools and cloud services.

---

## 📌 Table of Contents
1. [Project Overview](#project-overview)
2. [Project Structure](#project-structure)
3. [Setup & Installation](#setup--installation)
4. [Data Management with MongoDB](#data-management-with-mongodb)
5. [Logging, Exception Handling & EDA](#logging-exception-handling--eda)
6. [Data Ingestion Pipeline](#data-ingestion-pipeline)
7. [Data Validation, Transformation & Model Training](#data-validation-transformation--model-training)
8. [AWS Setup for Model Deployment](#aws-setup-for-model-deployment)
9. [Model Evaluation, Model Pusher & Prediction Pipeline](#model-evaluation-model-pusher--prediction-pipeline)
10. [CI/CD Automation](#cicd-automation)
11. [Project Workflow Summary](#project-workflow-summary)
12. [Additional Resources](#additional-resources)
13. [Connect](#connect)
14. [License](#license)

---

## 📁 Project Overview
The **Vehicle Insurance Data Pipeline** is designed to automate the workflow of a machine learning project:

- **Data Ingestion:** Fetch data from MongoDB.
- **Data Validation & Transformation:** Ensure data quality and create features.
- **Model Training & Evaluation:** Train ML models and measure performance.
- **Model Deployment:** Deploy models using AWS S3, EC2, and provide API access.
- **CI/CD Automation:** Use Docker, GitHub Actions, and AWS services for automated deployments.

---

## 🏗️ Project Structure

```text
MLOPS-project/
│
├── .github/workflows/         CI/CD pipelines
├── artifact/                  Saved artifacts like models
├── config/                    Configuration files
├── notebook/                  Jupyter notebooks for EDA & MongoDB demo
├── src/                       Source code (pipeline components)
├── static/css/                Static files for UI
├── templates/                 HTML templates for web UI
├── app.py                     API entry point
├── demo.py                    Demo for testing modules
├── Dockerfile                 Docker configuration
├── requirements.txt           Python dependencies
├── setup.py                   Package setup
├── pyproject.toml             Package metadata
├── template.py                Project template generator
└── README.md                  Project documentation
````

---

## 🔧 Setup & Installation

### 1. Create Project Template

```bash
python template.py
```

### 2. Set Up Virtual Environment

```bash
conda create -n vehicle python=3.10 -y
conda activate vehicle
pip install -r requirements.txt
pip list  # Verify packages
```

### 3. Package Management

* Configure `setup.py` and `pyproject.toml` for importing local packages.
* Refer to `crashcourse.txt` for details.

---

## 📊 Data Management with MongoDB

### MongoDB Atlas Configuration

1. Sign up for [MongoDB Atlas](https://www.mongodb.com/cloud/atlas).
2. Create a free **M0 cluster**.
3. Configure username & password.
4. Allow access from all IPs: `0.0.0.0/0`.
5. Save MongoDB connection string for Python.

### Push Data to MongoDB

* Add dataset in `notebook/`.
* Run `mongoDB_demo.ipynb` to upload data.
* Verify in MongoDB Atlas → **Database → Browse Collections**.

---

## 📝 Logging, Exception Handling & EDA

### Logging & Exception Handling

* Implement **logging** and **exception handling** modules.
* Test using `demo.py`.

### Exploratory Data Analysis (EDA) & Feature Engineering

* Analyze dataset using `EDA_FeatureEngg.ipynb`.
* Engineer features to improve model performance.

---

## 📥 Data Ingestion Pipeline

* MongoDB connection: `configuration/mongo_db_connections.py`
* Data ingestion components:

  * `data_access/`
  * `components/data_ingestion.py`
* Update entities:

  * `entity/config_entity.py`
  * `entity/artifact_entity.py`

### Environment Variables

```bash
# Bash
export MONGODB_URL="mongodb+srv://<username>:<password>@cluster.mongodb.net/dbname"
# PowerShell
$env:MONGODB_URL="mongodb+srv://<username>:<password>@cluster.mongodb.net/dbname"
```

---

## 🔍 Data Validation, Transformation & Model Training

### Data Validation

* Define schema: `config/schema.yaml`
* Implement validation in: `utils/main_utils.py`

### Data Transformation

* Implement in: `components/data_transformation.py`
* Use: `entity/estimator.py` for model objects.

### Model Training

* Implement in: `components/model_trainer.py` using `estimator.py`.

---

## 🌐 AWS Setup for Model Deployment

### AWS Configuration

1. Create IAM user with **AdministratorAccess**.
2. Configure credentials:

```bash
export AWS_ACCESS_KEY_ID="YOUR_AWS_ACCESS_KEY_ID"
export AWS_SECRET_ACCESS_KEY="YOUR_AWS_SECRET_ACCESS_KEY"
```

3. Create **S3 bucket**: `my-model-mlopsproj` (us-east-1).
4. Configure access in `constants/__init__.py`.

### Model Evaluation & S3

* Implement push/pull model functionality:

  * `src/aws_storage/`
  * `entity/s3_estimator.py`

---

## 🚀 Model Evaluation, Model Pusher & Prediction Pipeline

* Evaluate models → select best performer.
* Deploy model using **Model Pusher**.
* Create **Prediction Pipeline** integrated in `app.py`.
* Use `static/` & `templates/` folders for **web UI**.

---

## 🔄 CI/CD Automation

### Docker & GitHub Actions

* Create `Dockerfile` and `.dockerignore`.
* Configure GitHub Actions for CI/CD.
* Add AWS secrets in GitHub:

  * `AWS_ACCESS_KEY_ID`
  * `AWS_SECRET_ACCESS_KEY`
  * `AWS_DEFAULT_REGION`
  * `ECR_REPO`

### AWS EC2 & ECR

* Launch EC2 → Install Docker → Connect as GitHub self-hosted runner.
* Push Docker image to **ECR**.

### Access Application

```
http://<EC2_PUBLIC_IP>:5080
```

---

## 🎯 Project Workflow Summary

```
Data Ingestion ➔ Data Validation ➔ Data Transformation
        ➔ Model Training ➔ Model Evaluation ➔ Model Deployment
        ➔ CI/CD Automation (GitHub Actions, Docker, AWS EC2/ECR)
```

---

## 🛠️ Additional Resources

* `crashcourse.txt` – setup.py & pyproject.toml guide
* [MongoDB Documentation](https://docs.atlas.mongodb.com/)
* [AWS Documentation](https://docs.aws.amazon.com/)

---

```


<img width="1920" height="1080" alt="Screenshot (1093)" src="https://github.com/user-attachments/assets/4e0e4eb1-7a08-43b1-8309-8643cfefd8fb" />
<img width="1920" height="1080" alt="Screenshot (1091)" src="https://github.com/user-attachments/assets/356c0588-7f95-4e6e-be2b-bb09bb716cdf" />

<img width="1920" height="1080" alt="Screenshot (1090)" src="https://github.com/user-attachments/assets/032216ec-1e2b-495a-815f-acfb21ddc8f9" />
<img width="1920" height="1080" alt="Screenshot (1088)" src="https://github.com/user-attachments/assets/03b4ef62-5243-475c-be39-155211c24268" />


<img width="1920" height="1080" alt="Screenshot (1087)" src="https://github.com/user-attachments/assets/97e1173b-d6b3-4c26-94e4-4fed03e3e947" />
<img width="1920" height="1080" alt="Screenshot (1086)" src="https://github.com/user-attachments/assets/c574370c-bd87-40cd-8167-f686d567b302" />

<img width="1920" height="1080" alt="Screenshot (1085)" src="https://github.com/user-attachments/assets/176975a2-aefd-4c22-80ea-c2fe57d084f1" />
<img width="1920" height="1080" alt="Screenshot (1076)" src="https://github.com/user-attachments/assets/e16400c8-5289-4250-8a33-7330d1c9e90a" />


<img width="1920" height="1080" alt="Screenshot (1081)" src="https://github.com/user-attachments/assets/0a6d6c74-ba7d-486a-aa0a-4627d1f989ae" />
<img width="1920" height="1080" alt="Screenshot (1089)" src="https://github.com/user-attachments/assets/70d0e97b-7973-4f41-b787-2cf596091dcb" />

