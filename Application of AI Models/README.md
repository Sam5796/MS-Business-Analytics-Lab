# 🤖 Application of AI Models in Business (Deep Learning & GenAI)

## 📚 Course Overview
**Subject:** Application of AI Models
**Focus:** Leveraging unstructured data (Text & Images) to solve business problems. It progresses from Deep Learning foundations (Tensors, Dense Layers) to State-of-the-Art architectures (**Transformers, YOLO, Topic Modeling**) used in modern AI applications.

## 🛠 Tools & Tech Stack
-   **Deep Learning Frameworks:** TensorFlow/Keras, PyTorch
-   **Computer Vision:** OpenCV, YOLO (You Only Look Once), MobileNetV2, CNNs
-   **NLP:** **Hugging Face Transformers**, **LDA (Latent Dirichlet Allocation)**, TF-IDF
-   **Foundations:** Tensor operations, Data Representation (Scalars/Vectors/Matrices)

---

## 📂 Project Breakdown

### 🔹 Part 1: Deep Learning Foundations

#### Data Representation & EDA
**Goal:** Understanding how machines "see" data.
-   **🔑 Key Skills:** **Tensor Operations** (Scalars, Vectors, Matrices), reshaping data for Neural Networks, and Exploratory Data Analysis (EDA) on Airbnb datasets.
-   **Business Application:** Preparing raw business data for ingestion into deep learning pipelines.
-   **Files:**
    * `WData Representation_Shared.ipynb`
    * `EDA with Airbnb Listing Data_shared.ipynb`

#### Regression & Classification with Neural Nets
**Goal:** Building the first Neural Networks for prediction.
-   **🔑 Key Skills:** **Binary Classification** (Movie Reviews), **Regression** (Airbnb Price Prediction), Activation Functions (Sigmoid vs. Linear), Loss Functions (MSE vs. Binary Crossentropy).
-   **Business Application:** Automating decision-making (Approval/Denial) and price forecasting.
-   **Files:**
    * `Price Prediction with Airbnb Listing Data_shared.ipynb`
    * `Binary Classification_ Classifying Movie Reviews_shared.ipynb`

---

### 🔹 Part 2: Natural Language Processing (NLP)

#### NLP Foundations (Feature Engineering)
**Goal:** Converting raw text into machine-readable features.
-   **🔑 Key Skills:** **Bag of Words (BoW)**, **TF-IDF Vectorization**, **N-grams**, Tokenization.
-   **Business Application:** Creating search indexes and automated document tagging systems.
-   **File:** `NLP Foundations...ipynb`

#### Topic Modeling (Unsupervised Learning)
**Goal:** Discovering hidden themes in large document collections without labeling.
-   **🔑 Key Skills:** **Latent Dirichlet Allocation (LDA)**, Non-Negative Matrix Factorization (NMF), Coherence Scores.
-   **Business Application:** **Customer Insight Mining**—automatically clustering thousands of Airbnb reviews to find common complaints (e.g., "Cleanliness," "Check-in Process") without manual reading.
-   **Files:** `Topic Modeling with Airbnb Reviews_Shared.ipynb`

#### Advanced NLP with Transformers (Hugging Face)
**Goal:** Leveraging pre-trained Large Language Models (LLMs).
-   **🔑 Key Skills:** **Hugging Face Transformers**, **BERT/RoBERTa**, Transfer Learning for NLP.
-   **Business Application:** Next-gen sentiment analysis and automated text summarization.
-   **File:** `NLP with Hugging Face Transformers_Shared.ipynb`

---

### 🔹 Part 3: Computer Vision (Image Classification & Detection)

#### CNN Architectures (MNIST to CIFAR-10)
**Goal:** Building Convolutional Neural Networks to recognize visual patterns.
-   **🔑 Key Skills:** **Conv2D Layers**, MaxPooling, Dropout (Regularization), handling multi-class classification (Softmax).
-   **Business Application:** Optical Character Recognition (OCR) and automated visual sorting.
-   **Files:** `Image Classification...ipynb`, `AI_Group_In_Class_Exercise...ipynb`

#### WTransfer Learning with MobileNetV2
**Goal:** Using enterprise-grade models on small datasets.
-   **🔑 Key Skills:** **Transfer Learning**, Feature Extraction, Fine-Tuning, **MobileNetV2** (Lightweight models).
-   **Business Application:** Deploying AI on **Edge Devices** (IoT/Mobile) where processing power is limited.
-   **Files:** `Class Exe Transfer_Learning...ipynb`

#### Object Detection (YOLO)
**Goal:** **Safety Compliance.** Detecting objects in real-time video.
-   **🔑 Key Skills:** **YOLO (You Only Look Once)**, Bounding Box Regression, Custom Dataset Training.
-   **Business Application:** **Workplace Safety Monitoring**—detecting Hard Hats/PPE compliance on construction sites.
-   **Files:** `Object Detection with YOLO...ipynb`

---

## 🚀 AI Business Synthesis Matrix

| Business Goal | AI Technique | Real-World Application |
| :--- | :--- | :--- |
| **Customer Insight** | **Topic Modeling (LDA)** | Automatically grouping thousands of reviews to identify top complaints (e.g., "Wi-Fi issues"). |
| **Workplace Safety** | **Object Detection (YOLO)** | Real-time monitoring of PPE compliance (Hard Hats) to reduce liability. |
| **Customer Experience** | **Transformers (BERT)** | Analyzing complex sentiment/emotion in support tickets with near-human accuracy. |
| **Mobile Deployment** | **Transfer Learning** | Running image recognition on mobile apps without cloud latency. |
| **Forecasting** | **Neural Networks** | Predicting listing prices based on complex, non-linear feature interactions. |Contains coursework of Application of AI in Business
