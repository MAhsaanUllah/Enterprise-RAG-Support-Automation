# 🤖 Industrial SOP AI Copilot (RAG-Enabled)

[![n8n-Workflow](https://img.shields.io/badge/Orchestration-n8n-red)](https://n8n.io)
[![LLM-Gemini](https://img.shields.io/badge/Model-Gemini--2.5--Flash-blue)](https://deepmind.google/technologies/gemini/)
[![VectorDB-Pinecone](https://img.shields.io/badge/VectorDB-Pinecone-green)](https://www.pinecone.io/)

## 🏗 Business Use Case: IndusPrecision Engineering
**The Client:** A large-scale manufacturing plant in Gujranwala specializing in metal die-casting.
**The Challenge:** Maintenance engineers face significant downtime when machines like the **HP-500 Hydraulic Press** fail. Manuals are 500+ pages long, and searching for error codes (e.g., E-301, E-405) in a noisy factory is inefficient.
**The Solution:** An AI Agent that provides instant, proprietary troubleshooting steps directly via chat, ensuring machine downtime is minimized.

## 🛠 Technical Architecture
The system uses a **Retrieval-Augmented Generation (RAG)** approach:
- **Ingestion:** Proprietary manuals are pulled from **Google Docs API**.
- **Processing:** Data is chunked via **Default Data Loader** and converted to 768-dimensional vectors.
- **Storage:** Vectors are stored in a **Pinecone Serverless Index**.
- **Reasoning:** **Gemini 2.5 Flash** acts as the brain, using the Pinecone tool to retrieve context before answering.
- **Memory:** **Window Buffer Memory** tracks session IDs to handle multi-turn conversations.

## 📂 Project Structure
```text
├── workflows/
│   └── industrial_sop_agent.json  # The n8n workflow file
├── docs/
│   └── IndusPrecision_Technical_Manual_2026.docx          # Example SOPs for testing
└── README.md
```

## 🚀 Live Demo & Screenshots
[Insert Link to your Hugging Face Space here]

## 🧪 User Acceptance Testing (UAT)
You can test the agent's accuracy and safety logic with these scenarios:

| Category | Test Question | Expected Insight |
|----------|---|---|
| Safety | "Machine temp is 96°C, should I shut down?" | AI advises NOT to shut down to prevent piston seizure. |
| Proprietary | "What is the fix for Error E-301?" | Recommends the specific Blue Silicon O-Ring (BK-99). |
| Context | "What was the part number for it?" | AI remembers "it" refers to the O-ring from the previous turn. |

## 🛠 Setup Instructions
- Import the industrial_sop_agent.json into your n8n instance.
- Configure Credentials for Google Docs API, Pinecone, and Google Gemini (PaLM) API.
- Set the Pinecone mode to Insert for initial data loading, then switch to Retrieve for the Chat Agent.

## 🔮 Future Roadmap
- 📱 **WhatsApp Integration:** Connect via n8n WhatsApp node for on-field support.
- 👁️ **Visual Troubleshooting:** Image-to-text to identify machine parts via photos.
- 🗣️ **Voice-to-SOP:** Direct voice queries for hands-free operation.

