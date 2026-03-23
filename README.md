# Mental Health Conversational AI: Empathetic Fine-Tuning

## 📌 Project Overview
This project focuses on adapting a pre-trained Large Language Model (LLM) to act as an empathetic conversational agent. The objective is to shift the model's baseline behavior from simple factual responses to supportive, emotionally intelligent dialogue suitable for a mental health context.

## 📊 Dataset & Engineering
* **Dataset:** Facebook's `EmpatheticDialogues` (Filtered subset).
* **Objective:** Train the model to recognize user sentiment and reply with validating and comforting text.
* **Preprocessing:** Conversations were restructured into explicit `User: [Text] \n Bot: [Text]` prompt-completion pairs.
* **Data Split:** Implemented a strict 90/10 Train-Validation split to actively monitor generalization.

## 🧠 Model Architecture & Training
* **Base Model:** `DistilGPT2` (Chosen for its lightweight footprint and rapid inference capabilities).
* **Hardware:** NVIDIA T4 Tensor Core GPU.
* **Framework:** Hugging Face `Trainer` API.
* **Advanced Training Mechanics:**
  * **Early Stopping Callback:** Configured with a patience of 3 evaluation steps to autonomously halt training at peak validation performance, completely preventing overfitting.
  * **Learning Rate Optimization:** Set to `2e-5` with a `weight_decay` of 0.01 for stable convergence.
  * **Loss Optimization:** Monitored via Cross-Entropy Loss on both training and validation sets.

## 📈 Performance & Evaluation
The model achieved optimal convergence without overfitting, as evidenced by the validation loss tightly tracking the training loss until the Early Stopping mechanism engaged. 

*(See the `Loss_Curve.png` in this repository for the Training vs. Validation graph).*

## 💾 Deployment & Persistence
Engineered a custom cloud-storage pipeline to mount the runtime environment directly to Google Drive. This ensures the fine-tuned weights (`.safetensors`) and tokenizer configurations are saved persistently in real-time, preventing data loss from cloud instance timeouts.

## 📦 Model Access
Due to GitHub's file size constraints, the fine-tuned model weights and tokenizer configurations are hosted externally. 
* **Access the trained model here:** [Google Drive - EmpatheticBot_EarlyStop_V1](https://drive.google.com/drive/folders/1rgXLQA9HNeKZJ-R9hdhq6zZ-sHm2-9K6?usp=sharing)

## 🛠️ Tech Stack
* **Language:** Python
* **Libraries:** Transformers (Hugging Face), Datasets, Pandas, PyTorch, Gradio, Matplotlib
* **Pipeline:** CausalLM, Text-Generation

## 👩‍💻 Author
**Eshaal Hammad**
* **Email:** eshaalhammad234@gmail.com
