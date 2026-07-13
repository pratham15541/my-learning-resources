# AI and Machine Learning Resources

This folder contains resources, learning tracks, and core books for AI, Machine Learning, and LLM Engineering.

## Folder Layout

- [books/](books/README.md): Book summaries and recommended reading order for AI/ML learning.

## Focus Areas

- **Foundations**: Mathematics for ML, statistics, optimization, and basic ML algorithms in Python.
- **Deep Learning**: Neural network architectures, GNNs, and Reinforcement Learning.
- **LLM Engineering**: Designing, evaluation, fine-tuning, and building applications with Large Language Models.
- **MLOps & Systems**: Scaling data pipelines, training platforms, deployment topologies, and hardware acceleration.

---

## AI/ML Design Decision Framework

When building real-world AI and Machine Learning applications, you must evaluate trade-offs across multiple operational axes:

### 1. The Modeling Tradeoff Axes

- **Data Availability**: Do we have labeled data (supervised) or only unlabeled text (pretraining/unsupervised)?
- **Latency Budget**: Must predictions run in sub-100ms (online inference) or can they run offline (batch)?
- **Compute and Storage**: Are we deploying to resource-constrained devices (edge) or scalable cloud clusters?
- **Interpretability vs Performance**: Do we need to explain *why* a model made a decision (linear models/trees) or is raw accuracy paramount (deep learning)?

---

### 2. LLM vs Custom Traditional ML

**Large Language Models (LLMs) (e.g., GPT, Llama, Claude):**
- *Advantages*: zero-shot capabilities, handles unstructured text beautifully, rapid prototyping.
- *Disadvantages*: high latency, high API costs, hallucination risk, lack of deterministic guarantees.

**Traditional/Custom ML (e.g., XGBoost, Scikit-Learn, Custom BERT):**
- *Advantages*: ultra-fast inference (sub-10ms), low compute requirements, highly interpretable, deterministic testing.
- *Disadvantages*: requires extensive labeled training data, limited context reasoning, high feature engineering effort.

---

### 3. CPU vs GPU Inference

**CPU-Based Inference:**
- *Best For*: tabular models (XGBoost, Random Forest), lightweight deep learning models, low-concurrency workloads.
- *Operational Profile*: cheap, highly available, easy to scale horizontally.

**GPU-Based Inference:**
- *Best For*: LLMs, large transformer models, high-throughput image/video processing.
- *Operational Profile*: expensive, cold-start delays, complex memory management (VRAM limits), requires batching pipelines.

---

### 4. Real-time vs Batch Inference

**Real-Time (Online) Inference:**
- *Design*: Model exposed via HTTP/gRPC endpoint or loaded directly in memory.
- *Challenge*: Scaling compute dynamically under sudden traffic spikes; keeping model size small enough for fast loading.

**Batch (Offline) Inference:**
- *Design*: Cron jobs or event-driven workers processing records in bulk from data stores.
- *Challenge*: Managing data consistency; scheduling compute clusters efficiently to minimize idle time costs.

---

## Phased Learning Roadmap

### Phase 1 - Foundations & Core ML
- **Goal**: Master the math and classic algorithms.
- **Resources**:
  - [Mathematics for Machine Learning](books/mathematics-for-ml-book.pdf)
  - [Python Machine Learning by Example](books/python-machine-learning-by-example-3.pdf)
  - [Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow](books/Hands-On_Machine_Learning_with_Scikit-Learn_Keras_and_TensorFlow_3rd_Edition_-_Aurelien_Geron.pdf)

### Phase 2 - Deep Learning & Specializations
- **Goal**: Understand neural architectures, GNNs, and RL basics.
- **Resources**:
  - [Deep Learning](books/Deep%2BLearning%2BIan%2BGoodfellow.pdf)
  - [Hands-On Graph Neural Networks Using Python](books/HandsOnGraphNeuralNetworksUsingPython.pdf)
  - [Reinforcement Learning: An Introduction](books/SuttonBartoIPRLBook2ndEd.pdf)

### Phase 3 - LLMs & Application Engineering
- **Goal**: Learn to build application layers around Foundation Models.
- **Resources**:
  - [Natural Language Processing with Transformers](books/Natural%20Language%20Processing%20with%20Transformers%20Building%20Language%20Applications%20with%20Hugging%20Face%20by%20Lewis%20Tunstall%20%20Leandro%20von%20Werra%20%20Thomas%20Wolf.pdf)
  - [Hands-On Large Language Models](books/Hands-On_Large_Language_Models_-_Jay_Alammar.pdf)
  - [Building LLMs for Production](books/Building%20LLMS%20for%20production.pdf)
  - [AI Engineering: Building Applications With Foundation Models](books/AI%20Engineering_%20Building%20Applications%20With%20Foundation%20Models%20by%20Chip%20Huyen%20(1).pdf)

### Phase 4 - Data Engineering & AI System Design
- **Goal**: Architect end-to-end production ML and Generative AI systems.
- **Resources**:
  - [Fundamentals of Data Engineering](books/Fundamentals%20of%20Data%20Engineering%20(Reis,%20JoeHousley,%20Matt)%20(Z-Library).pdf)
  - [Designing Machine Learning Systems](books/Designing%20Machine%20Learning%20Systems.pdf)
  - [Generative AI System Design Interview](books/generative-ai-system-design-interview.pdf)
