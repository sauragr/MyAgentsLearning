# 🤖 MyAgentsLearning

A hands-on repository for learning and building **LLM-powered AI agents** using Python, LangChain, LangGraph, Groq, Tavily, tool calling, memory, persistence, streaming, human-in-the-loop workflows, and multi-step research pipelines.

The repository focuses on understanding **how agentic AI systems work internally** — from basic LLM tool calling to stateful, interruptible, and multi-step agent workflows.

---

## 🚀 What This Repository Covers

This repository explores the core building blocks of modern AI agent systems:

* LLM-powered agents
* Function / tool calling
* Tool execution workflows
* Conversational memory
* Stateful agent graphs
* LangGraph state management
* Persistence and checkpointing
* Streaming agent execution
* Human-in-the-loop workflows
* Web search and information retrieval
* Structured LLM outputs
* Multi-step research agents
* Reflection and iterative generation
* Agent workflow orchestration

---

## 🧠 Projects

### 1. 🔧 Agents & Tools

**Notebook:** `Agents_Tools.ipynb`

A foundational implementation exploring how an LLM can dynamically select and execute external tools.

#### Key Concepts

* LLM tool calling
* JSON Schema function definitions
* Tool selection
* Dynamic argument generation
* Python function execution
* Conversational message history
* Tool-result injection
* Multi-step LLM → Tool → LLM workflows

#### Workflow

```text
User Query
    ↓
LLM
    ↓
Determine Required Tool
    ↓
Generate Tool Call
    ↓
Execute Python Function
    ↓
Return Tool Result
    ↓
LLM
    ↓
Final Response
```

This project establishes the foundation for understanding how modern tool-using AI agents operate.

---

### 2. 👤 Human-in-the-Loop Agent

**Notebook:** `HumanInTheLoop.ipynb`

A stateful agent workflow that introduces **human oversight into agent execution**.

The agent can use external tools such as web search, but execution can be paused before a tool call and resumed after receiving human approval.

#### Key Concepts

* LangGraph
* LangChain
* Groq
* Tavily
* Human-in-the-loop
* Agent state
* Tool calling
* Interrupt/resume workflows
* Thread-based execution
* Streaming graph execution

#### Workflow

```text
User Request
     ↓
Agent
     ↓
Determine Required Tool
     ↓
Human Approval
     ↓
 ┌───────────────┐
 │               │
Approve        Reject
 │               │
 ↓               ↓
Execute Tool   Stop
 │
 ↓
Tool Result
 │
 ↓
Agent
 │
 ↓
Final Response
```

The project demonstrates how agent execution can be made **controllable and reviewable** instead of allowing every tool action to execute automatically.

LangGraph supports interrupting execution, checkpointing state, and later resuming the same workflow.

---

### 3. 💾 Persistence & Streaming

**Notebook:** `Persistence&Streaming.ipynb`

An exploration of **state persistence and streaming execution** for LangGraph-based agents.

The project uses checkpointing and memory components to maintain agent state across executions and uses thread IDs to maintain independent execution contexts.

#### Key Concepts

* LangGraph
* Stateful agents
* Checkpointing
* `InMemorySaver`
* `InMemoryStore`
* Thread-based execution
* Streaming
* Tool calling
* Agent state management
* Tavily web search

#### Architecture

```text
             ┌───────────────┐
             │   User Query  │
             └───────┬───────┘
                     ↓
              ┌─────────────┐
              │    Agent    │
              └──────┬──────┘
                     ↓
             ┌───────────────┐
             │ Tool Required?│
             └───────┬───────┘
                     ↓
              ┌─────────────┐
              │    Tools    │
              └──────┬──────┘
                     ↓
              ┌─────────────┐
              │ Agent State │
              └──────┬──────┘
                     ↓
             ┌───────────────┐
             │   Checkpoint  │
             └──────┬────────┘
                     ↓
              Final Response
```

This project focuses on an important production-agent concept: **maintaining execution state rather than treating every LLM call as an isolated request**.

---

### 4. 🔎 Researcher Agent

**Notebook:** `Researcher.ipynb`

A multi-step research agent that combines **planning, web search, information aggregation, generation, and reflection**.

Instead of directly answering a question, the system decomposes the research process into multiple stages.

#### Key Concepts

* LangGraph
* LangChain
* Groq
* Tavily
* Pydantic
* Structured LLM output
* Query generation
* Web research
* Information aggregation
* Content generation
* Reflection
* Iterative improvement
* Agent orchestration

#### Research Pipeline

```text
                  User Task
                     ↓
              Research Planner
                     ↓
           Generate Search Queries
                     ↓
              Tavily Web Search
                     ↓
          Aggregate Retrieved Data
                     ↓
             Content Generation
                     ↓
                Reflection
                     ↓
             Improved Output
```

The workflow separates research planning, retrieval, generation, and reflection into modular stages.

This demonstrates how an LLM can be used not only as a chatbot, but as a component inside a larger **agentic workflow**.

---

### 5. 🧩 LangGraph Agent

**Directory:** `Langgraph_Agent/`

This section contains additional experimentation with **LangGraph-based agent architecture and workflow orchestration**.

The goal is to understand how graph-based execution can be used to model agents as a collection of interconnected states and actions.

#### Focus Areas

* LangGraph
* Agent state
* Graph-based workflows
* Nodes and edges
* Agent orchestration
* Tool integration
* Stateful execution

---

# 🛠️ Technology Stack

| Technology           | Purpose                            |
| -------------------- | ---------------------------------- |
| **Python**           | Core programming language          |
| **LangChain**        | LLM and tool integration           |
| **LangGraph**        | Stateful agent orchestration       |
| **Groq**             | LLM inference                      |
| **Tavily**           | Web search / information retrieval |
| **Pydantic**         | Structured output validation       |
| **Jupyter Notebook** | Experimentation and prototyping    |

---

# 🏗️ Agent Architecture Concepts

The projects progressively explore different levels of agent complexity.

```text
                 ┌──────────────────────┐
                 │       LLM Agent      │
                 └──────────┬───────────┘
                            │
                  ┌─────────▼─────────┐
                  │   Tool Calling    │
                  └─────────┬─────────┘
                            │
                  ┌─────────▼─────────┐
                  │      Memory       │
                  └─────────┬─────────┘
                            │
                  ┌─────────▼─────────┐
                  │   Agent State     │
                  └─────────┬─────────┘
                            │
              ┌─────────────▼─────────────┐
              │   LangGraph Workflows     │
              └─────────────┬─────────────┘
                            │
              ┌─────────────▼─────────────┐
              │ Persistence & Streaming   │
              └─────────────┬─────────────┘
                            │
              ┌─────────────▼─────────────┐
              │ Human-in-the-Loop        │
              └─────────────┬─────────────┘
                            │
              ┌─────────────▼─────────────┐
              │ Multi-Step Research      │
              └───────────────────────────┘
```

---

# 📚 Learning Progression

The repository follows a progression from simple LLM applications toward more advanced agent architectures:

### Level 1 — LLM + Tools

Learn how an LLM can decide when and how to call external functions.

### Level 2 — Memory

Maintain conversation history and state across multiple interactions.

### Level 3 — Agent Graphs

Represent agent workflows using nodes, edges, and shared state with LangGraph.

### Level 4 — Persistence & Streaming

Persist execution state and observe intermediate agent execution.

### Level 5 — Human Oversight

Pause agent execution and require human approval before executing selected actions.

### Level 6 — Research Agents

Combine planning, retrieval, generation, and reflection into a multi-step workflow.

---

# 🎯 Key Engineering Concepts

Through these projects, the repository explores:

**Agent Architecture**

* Agent loops
* State machines
* Graph-based workflows
* Tool routing
* Workflow orchestration

**LLM Engineering**

* Prompt design
* Function calling
* Structured outputs
* Context management
* Multi-turn conversations

**Agent State**

* Message history
* Thread IDs
* Checkpoints
* Memory
* State persistence

**Tool Integration**

* Python tools
* Web search
* Dynamic tool selection
* Tool-result handling

**Agent Reliability**

* Human approval
* Interrupt/resume execution
* Structured output validation
* Reflection
* Iterative generation

---

# 🔬 Why This Repository?

The objective is to move beyond simply calling an LLM API and understand the engineering principles behind **agentic AI systems**.

The projects progressively answer questions such as:

> How does an LLM decide when to use a tool?

> How does an agent maintain state?

> How can an agent pause and resume execution?

> How can multiple agent steps be orchestrated?

> How can external information be incorporated into an agent workflow?

> How can generated outputs be reviewed and improved?

---

# 📂 Repository Structure

```text
MyAgentsLearning/
│
├── Agents_Tools.ipynb
│
├── HumanInTheLoop.ipynb
│
├── Persistence&Streaming.ipynb
│
├── Researcher.ipynb
│
└── Langgraph_Agent/
```

---

# ⚙️ Getting Started

## 1. Clone the repository

```bash
git clone https://github.com/sauragr/MyAgentsLearning.git
cd MyAgentsLearning
```

## 2. Create a virtual environment

```bash
python -m venv .venv
```

### Windows

```bash
.venv\Scripts\activate
```

### Linux / macOS

```bash
source .venv/bin/activate
```

## 3. Install dependencies

Install the libraries required by the notebooks:

```bash
pip install langchain langgraph langchain-groq tavily-python pydantic jupyter
```

## 4. Configure API Keys

Create environment variables for the services used by the notebooks.

```bash
GROQ_API_KEY="your_groq_api_key"
TAVILY_API_KEY="your_tavily_api_key"
```

> Never commit API keys or other secrets to the repository.

## 5. Launch Jupyter

```bash
jupyter notebook
```

Open the notebooks and run the projects individually.

---

# 🔑 Environment Variables

| Variable         | Purpose                        |
| ---------------- | ------------------------------ |
| `GROQ_API_KEY`   | Access Groq-hosted LLMs        |
| `TAVILY_API_KEY` | Enable web search capabilities |

---

# 📈 Future Improvements

Planned areas for extending this repository include:

* [ ] Add persistent database-backed checkpoints
* [ ] Add long-term agent memory
* [ ] Add agent evaluation and observability
* [ ] Add automated tests for agent workflows
* [ ] Add FastAPI interfaces for selected agents
* [ ] Add Streamlit interfaces for interactive agents
* [ ] Add RAG-based agent workflows
* [ ] Add multi-agent collaboration
* [ ] Add structured logging and tracing
* [ ] Add Docker-based deployment
* [ ] Add agent evaluation datasets
* [ ] Add latency and token-usage tracking

---

# 📌 Skills Demonstrated

**Programming:**
Python · API Integration · JSON · Pydantic

**LLM / Generative AI:**
LLMs · Prompt Engineering · Function Calling · Structured Outputs · Context Management

**AI Agents:**
AI Agents · Tool Calling · Agent State · Memory · Human-in-the-Loop · Reflection · Agent Orchestration

**Frameworks:**
LangChain · LangGraph

**Tools & APIs:**
Groq · Tavily · Jupyter

**Engineering Concepts:**
State Management · Checkpointing · Streaming · Modular Workflows · Interrupt/Resume Execution

---

# 👨‍💻 Author

**Saurabh Agrawal**

Data Science / AI Engineer focused on **LLM applications, AI agents, RAG systems, and intelligent automation**.

---

⭐ If you find this repository useful, feel free to explore the notebooks and experiment with the agent architectures.
