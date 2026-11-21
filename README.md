 leverages Large Language Models (LLMs) to simulate a full medical consultation team. It mitigates context collapse using a **Residual Discussion Structure** and employs a **Self-Evolving Mechanism** via dual knowledge bases (CorrectKB & ChainKB) to accumulate medical experience.

  * **👁️ Multimodal Support:** Added Vision-Language Model (VLM) integration. Specialists can now analyze uploaded medical images (CT, MRI, X-ray) alongside text descriptions in the first consultation round.
  * **🔓 Open-Ended QA:** The system now supports and evaluates complex, free-form diagnostic answers (Open-Ended) rather than just multiple-choice questions.
  * **🛠️ Tool Usage:** Specialists are now equipped with **DuckDuckGo** and **PubMed** tools to autonomously verify facts and retrieve external evidence during reasoning.

## ✨ Key Features

  * **👨‍⚕️ Multi-Role Specialists:** Dynamically assigns specialists (e.g., Cardiologist, Neurologist) based on the patient case.
  * **🧠 Context Engineering:** A **Lead Physician** agent synthesizes discussions into structured residual context (*Consistency, Conflict, Independence, Integration*) to reduce cognitive load.
  * **🔄 Self-Evolution:**
      * **CorrectKB:** Stores successful reasoning patterns.
      * **ChainKB:** Stores reflection and error analysis from incorrect diagnoses.
  * **🛡️ Safety & Ethics:** A dedicated reviewer ensures consensus convergence and output safety.



pip install -r requirements.txt


### 3\. Run the System

```bash
streamlit run app.py
```

## 📂 Project Structure

  * **`app.py`**: Streamlit UI for case entry, **image upload**, and training visualization.
  * **`workflow.py`**: LangGraph state machine (Triage $\to$ Consultation $\to$ Safety Check).
  * **`agents.py`**: Agent definitions including **VLM handling**, **Tool callbacks**, and strict output formatting.
  * **`knowledge_base.py`**: Dual-memory vector storage (FAISS) for experience retrieval.
  * **`tools.py`**: **New** integration for Web Search and PubMed tools.

## 🎓 Training Mode

1.  **Upload Image** (Optional) and text description.
2.  Input the **Ground Truth** (Correct Diagnosis).
3.  The system automatically grades the consultation:
      * **Correct:** Saves reasoning to `CorrectKB`.
      * **Incorrect:** Performs Chain-of-Thought reflection and saves to `ChainKB`.
  
