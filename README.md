# Quantum Backend Recommender

This repository contains our Python implementation of a **machine learning system** designed to **recommend the most suitable IBM Quantum backend** for executing a given quantum circuit.
The project combines **quantum circuit simulation** with **machine learning techniques**, including both classical algorithms and deep learning models, to recommend the most suitable backend based on circuit properties and backend performance metrics.

---

## Motivation

Running a quantum circuit on the right backend is **critical** for accurate results and efficient performance.
Different IBM quantum computers vary in qubit counts, error rates, and connectivity, making backend selection a **non-trivial problem**.

* Train models to **recommend the optimal backend**, reducing execution cost and queue times.
* Build a **dataset** by simulating circuits on IBM backends to capture execution properties.
* Compare **classical ML models** and **deep learning approaches** for backend prediction.
* Explore the intersection of **quantum computing** and **machine learning**.
* Building a foundation for future **quantum workload optimization tools**.

---

## Repository Contents

### **1. Generating the Dataset.ipynb**

This notebook creates datasets for training and testing machine learning models designed to recommend the best IBM quantum computer backend for a given quantum circuit.
Key steps include:

* **Simulating quantum circuits** using IBM Qiskit to represent realistic execution workloads.
* Collecting **backend characteristics** (e.g., qubit count, error rates, gate fidelity).
* Generating a labeled dataset by pairing circuit requirements with compatible backend performance.
* Produces two versions of the dataset: a small set for rapid experimentation (2,000 samples) and a large set for final model training (17,000 samples).

---

### **2. 2000 data.txt**

* A compact dataset containing **2,000 samples**, generated in the first notebook.
* Useful for quick prototyping and debugging, as it allows models to be trained and evaluated faster.
* Each row includes:

  * Circuit properties (e.g., number of qubits, depth, gate types).
  * Backend properties.
  * The target backend label (the “best match” for that circuit).

---

### **3. classical models.ipynb**

This notebook implements **classical machine learning algorithms** to predict the best backend given a circuit’s features.
Detailed contents:

* Data preprocessing:

  * Normalizing numeric features.
  * Handling categorical data related to backend identifiers.
* Implements and evaluates classical algorithms, including:

  * **Decision Trees** – interpretable baseline model.
  * **Random Forests** – ensemble method for higher accuracy.
  * **XGBoost** – optimized gradient boosting for top-tier performance.
* Includes **model evaluation** with accuracy, confusion matrices, and comparison across models.
* Provides early insights into feature importance, showing which circuit properties most strongly influence backend selection.

---

### **4. NN models.ipynb**

This notebook introduces **deep learning approaches** using Keras and TensorFlow.
It focuses on building a more flexible, generalizable system:

* **Model Architecture Design:**

  * Fully connected neural networks with customizable layer sizes.
  * Dropout and batch normalization for regularization.
* **Training pipeline:**

  * Adam optimizer, learning rate scheduling, and early stopping.
  * Loss functions designed for multi-class classification.
* **Comparison with classical models:**

  * Evaluates whether deep learning significantly improves performance over tree-based methods.
  * Visualizes training/validation loss and accuracy curves.
* Supports both the small (2,000 sample) and large (17,000 sample) datasets.

---

### **5. 17000 data.txt**

* A **large-scale dataset** containing **17,000 samples** generated from extensive simulations.
* Designed for training high-capacity models such as neural networks without overfitting.
* Reflects a wide range of circuit complexities and backend configurations, making it ideal for production-level experiments.

---

### **6. Updated Models - Latest Outcomes (so far).ipynb**

The final notebook consolidates everything into a **single, up-to-date workflow**:

* Trains both classical and neural network models on the **17,000-sample dataset**.
* Integrates the best preprocessing pipelines discovered in earlier notebooks.
* Performs **comprehensive evaluation**, including:

  * Accuracy, precision, recall, and F1 scores.
  * Backend-specific performance breakdowns.
  * Visualizations of confusion matrices and performance trends.
* Records **latest experimental outcomes**, providing a reference point for future improvements.
* Includes notes on observed challenges, such as model bias toward certain backend configurations.

---

## Requirements

Install dependencies with:

```bash
pip install qiskit scikit-learn tensorflow keras xgboost numpy matplotlib pandas
```

---

## Getting Started

1. **Clone the repository:**

```bash
git clone https://github.com/yourusername/quantum-backend-recommender.git
cd quantum-backend-recommender
```

2. **Run the dataset generation notebook:**

Open `Generating the Dataset.ipynb` in Jupyter Notebook or Jupyter Lab and execute it to create the required datasets.

3. **Train classical ML models:**

Run the notebook:

```bash
jupyter notebook "classical models.ipynb"
```

4. **Train deep learning models:**

Run the notebook:

```bash
jupyter notebook "NN models.ipynb"
```

5. **View final results:**

Open `Updated Models - Latest Outcomes (so far).ipynb` to see the most recent findings and comparisons.

---

## Results

* **Classical ML Models:** Best accuracy around **22.5%** using SVM and ensembles.
* **Deep Learning Models:** Comparable performance (\~21.9%), with room for improvement through advanced architectures.
* The **expanded dataset (17000 samples)** significantly improved model stability and generalization.

Key findings so far:

* Classical algorithms like **Random Forests** and **XGBoost** provide strong baselines with interpretable outputs.
* Deep learning models achieve **higher accuracy** on the larger dataset but require careful tuning to prevent overfitting.
* Feature importance analysis highlights that:

  * Circuit depth and qubit count are major predictors of backend choice.
  * Backend noise metrics heavily influence decisions.

---

## Reference

* **IBM Qiskit:** [https://qiskit.org/](https://qiskit.org/)
* **Scikit-learn:** [https://scikit-learn.org/](https://scikit-learn.org/)
* **TensorFlow/Keras:** [https://www.tensorflow.org/](https://www.tensorflow.org/)
* **XGBoost:** [https://xgboost.ai/](https://xgboost.ai/)

---

## Acknowledgments

Special thanks to the open-source communities behind Qiskit, Scikit-learn, TensorFlow, and PyTorch for their invaluable tools.



