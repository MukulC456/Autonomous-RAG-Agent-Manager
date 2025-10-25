# Autonomous-RAG-Agent-Manager
Overview
This project implements an autonomous Retrieval-Augmented Generation (RAG) AI Agent capable of learning from uploaded documents, storing context in Pinecone, reasoning with LangChain, and exposing actions through Model Context Protocol (MCP) for integration with external AI clients (like Claude Desktop or Cursor). Built using n8n, it combines low-code automation and agentic reasoning to deliver a self-managing AI knowledge assistant.

# Key Features
1. RAG-Powered Context Retrieval – Embed and query any text or document using Pinecone and OpenAI embeddings.
2. Autonomous Workflow Automation – Dynamically retrieve, process, and answer user queries via n8n workflows.
3. MCP Integration – Serve or consume agent tools using Model Context Protocol for seamless external interaction.
4. LangChain Reasoning Layer – Use prompt templates and retrieval chains to provide contextual, explainable AI responses.
5. Extensible Nodes – Connect file systems, Google Drive, Notion, or Slack as new data and communication channels.

# System Architecture
1. Data Layer (Pinecone)-	Vector store for embeddings & semantic search
2. Agent Layer	(LangChain)-	Handles reasoning, retrieval chains, and LLM memory
3. Orchestration Layer	(n8n)-	Coordinates triggers, data pipelines, and logic
4. Interface Layer	(MCP)-	Exposes and manages agent tools for external clients

# Workflow Description
1. Document Processing
- Upload any PDF or text file through an HTTP or Google Drive trigger.
- Content is chunked, embedded using OpenAI API, and stored in Pinecone.
  
2. Retrieval-Augmented Generation (RAG)
- Queries are transformed into embeddings.
- Pinecone returns the most relevant document chunks.
- LangChain RetrievalQA composes a contextually accurate answer.

3. MCP Agent Exposure
- The n8n workflow acts as an MCP Server.
- External LLMs (e.g., Claude Desktop, Cursor) can query the agent using standardized MCP actions like: query_knowledge_base, create_index, fetch_recent_context.

4. Response Delivery
- n8n output node returns final answers to the UI or API consumer.

# Tech Stack
1. n8n – Workflow automation & orchestration
2. LangChain – Cognitive framework for reasoning and tool use
3. Pinecone – Vector store for semantic memory
4. MCP – Model Context Protocol for multi-agent tool interoperability
5. OpenAI / Gemini API – For LLM inference and embedding creation
