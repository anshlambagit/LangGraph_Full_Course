# LangGraph Tutorial Series 📚

A comprehensive, hands-on tutorial series for learning **LangGraph** - a powerful framework for building stateful, multi-agent applications with Large Language Models (LLMs).

![LangGraph Logo](https://raw.githubusercontent.com/langchain-ai/langgraph/main/docs/static/img/langgraph-logo.png)

## 🚀 What is LangGraph?

LangGraph is a library for building stateful, multi-actor applications with LLMs, built on top of [LangChain](https://www.langchain.com/). It extends the LangChain Expression Language with the ability to coordinate multiple chains (or actors) across multiple steps of computation in a cyclic manner.

## 📋 Table of Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Project Structure](#project-structure)
- [Tutorial Overview](#tutorial-overview)
- [Getting Started](#getting-started)
- [Notebooks](#notebooks)
- [Key Concepts Covered](#key-concepts-covered)
- [Dependencies](#dependencies)
- [Configuration](#configuration)
- [Usage Examples](#usage-examples)
- [Contributing](#contributing)
- [License](#license)
- [Resources](#resources)

## ✨ Features

- **Stateful Applications**: Build applications that maintain state across multiple interactions
- **Multi-Agent Systems**: Coordinate multiple LLM-powered agents
- **Cyclic Computation**: Handle complex workflows with loops and conditional logic
- **Human-in-the-Loop**: Integrate human feedback and approval workflows
- **Memory Management**: Persistent state with various checkpointing options
- **Tool Integration**: Connect with external APIs and services
- **Parallel Execution**: Run multiple tasks concurrently
- **Router Patterns**: Intelligent routing based on content and context

## 📋 Prerequisites

- **Python 3.12+**
- **OpenAI API Key** (for LLM interactions)
- **Anthropic API Key** (optional, for Claude models)
- Basic understanding of Python programming
- Familiarity with Jupyter Notebooks

## 🛠️ Installation

### 1. Clone the Repository

```bash
git clone https://github.com/anshlambagit/LangGraph_Full_Course.git
cd langgraph-tutorial
```

### 2. Create Virtual Environment

```bash
# Windows
python -m venv .venv
.venv\Scripts\activate

# Linux/Mac
python -m venv .venv
source .venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

Or using the modern Python package manager:

```bash
pip install -e .
```

### 4. Environment Setup

Create a `.env` file in the root directory:

```env
OPENAI_API_KEY=your_openai_api_key_here
ANTHROPIC_API_KEY=your_anthropic_api_key_here  # Optional
```

## 📁 Project Structure

```
langgraph-tutorial/
│
├── pyproject.toml          # Project configuration
├── requirements.txt        # Python dependencies
├── README.md              # This file
│
└── Notebooks/             # Tutorial notebooks
    ├── 1_First_Graph.ipynb
    ├── 2_Pydantic.ipynb
    ├── 3_messages.ipynb
    ├── 4_Prompts&Chains.ipynb
    ├── 5_Tools&Binding.ipynb
    ├── 6_ReAct.ipynb
    ├── 7_Parralelization.ipynb
    ├── 8_Router.ipynb
    ├── 9_Orchestrator_Worker.ipynb
    ├── 10_Generator_Evaluator.ipynb
    ├── 11_Memory.ipynb
    └── 12_HumanInLoop.ipynb
```

## 🎯 Tutorial Overview

This tutorial series takes you from LangGraph basics to advanced patterns through **12 progressive notebooks**:

### Beginner Level
- **Notebook 1**: Your first LangGraph - Basic graph creation and execution
- **Notebook 2**: Pydantic schemas - Type-safe state management
- **Notebook 3**: Messages - Working with conversational AI

### Intermediate Level
- **Notebook 4**: Prompts & Chains - Advanced prompt engineering
- **Notebook 5**: Tools & Binding - Integrating external tools
- **Notebook 6**: ReAct Pattern - Reasoning and acting agents
- **Notebook 7**: Parallelization - Concurrent task execution

### Advanced Level
- **Notebook 8**: Router - Intelligent routing logic
- **Notebook 9**: Orchestrator-Worker - Multi-agent coordination
- **Notebook 10**: Generator-Evaluator - Quality assurance patterns
- **Notebook 11**: Memory - State persistence and checkpoints
- **Notebook 12**: Human-in-the-Loop - Human feedback integration

## 🚀 Getting Started

1. **Start with Notebook 1**: Begin with the fundamentals
2. **Follow the sequence**: Each notebook builds on the previous one
3. **Experiment**: Modify the code and see how it affects behavior
4. **Take breaks**: The concepts build progressively

### Quick Start

```python
from langgraph.graph import StateGraph, START, END
from typing import TypedDict

# Define your state schema
class MyState(TypedDict):
    message: str

# Create a simple node function
def hello_node(state: MyState) -> MyState:
    return {"message": f"Hello, {state['message']}!"}

# Build and compile the graph
graph = StateGraph(MyState)
graph.add_node("hello", hello_node)
graph.add_edge(START, "hello")
graph.add_edge("hello", END)

app = graph.compile()

# Run the graph
result = app.invoke({"message": "World"})
print(result)  # {'message': 'Hello, World!'}
```

## 📚 Notebooks

### 1. First Graph
- Basic LangGraph concepts
- State definition with TypedDict
- Node functions and graph construction
- Graph compilation and execution

### 2. Pydantic
- Advanced state schemas
- Pydantic models for type safety
- Validation and serialization

### 3. Messages
- LangChain message types
- Conversational patterns
- Message history management

### 4. Prompts & Chains
- Prompt templates
- Chain composition
- Advanced prompt engineering techniques

### 5. Tools & Binding
- Tool creation and integration
- Function binding to LLMs
- External API connections

### 6. ReAct
- Reasoning and Acting pattern
- Agent-based decision making
- Tool use for problem solving

### 7. Parallelization
- Concurrent task execution
- Fan-out/fan-in patterns
- Performance optimization

### 8. Router
- Conditional routing logic
- Content-based decisions
- Dynamic workflow control

### 9. Orchestrator-Worker
- Multi-agent architectures
- Task delegation
- Coordinator patterns

### 10. Generator-Evaluator
- Quality assurance
- Self-improvement loops
- Iterative refinement

### 11. Memory
- State persistence
- Checkpointing strategies
- Long-term memory management

### 12. Human-in-the-Loop
- Human feedback integration
- Approval workflows
- Interactive agents

## 🔑 Key Concepts Covered

- **State Management**: TypedDict, Pydantic models
- **Graph Construction**: Nodes, edges, conditional edges
- **Execution Patterns**: Sequential, parallel, conditional
- **Tool Integration**: Custom tools, API connections
- **Memory Systems**: In-memory, persistent checkpoints
- **Human Interaction**: Interrupts, approvals, feedback
- **Multi-Agent Patterns**: Orchestrator-worker, router patterns
- **Quality Assurance**: Generator-evaluator loops

## 📦 Dependencies

### Core Dependencies
- `langgraph>=1.0.8` - Main LangGraph library
- `langchain>=1.2.10` - LangChain framework
- `langchain-openai>=1.1.9` - OpenAI integration
- `langchain-anthropic>=1.3.3` - Anthropic Claude integration

### Tool Integrations
- `duckduckgo-search>=8.1.1` - Web search capabilities
- `wikipedia>=1.4.0` - Wikipedia API access
- `arxiv>=2.4.0` - Academic paper search
- `pymupdf>=1.27.1` - PDF processing

### Development Tools
- `jupyter` - Interactive notebooks
- `python-dotenv` - Environment variable management
- `ipykernel` - Jupyter kernel for Python

## ⚙️ Configuration

### Environment Variables

Create a `.env` file with your API keys:

```env
# Required
OPENAI_API_KEY=sk-your-openai-key-here

# Optional
ANTHROPIC_API_KEY=sk-ant-your-anthropic-key-here
```

### Python Version

This project requires **Python 3.12 or higher**. Check your version:

```bash
python --version
```

## 💡 Usage Examples

### Basic Chatbot
```python
from langgraph.graph import StateGraph
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(model="gpt-4")

def chatbot(state):
    response = llm.invoke(state["messages"])
    return {"messages": state["messages"] + [response]}

graph = StateGraph({"messages": []})
graph.add_node("chatbot", chatbot)
# ... add edges and compile
```

### Tool-Using Agent
```python
from langchain.tools import tool
from langgraph import StateGraph

@tool
def search_web(query: str) -> str:
    # Implement web search
    pass

tools = [search_web]
llm_with_tools = llm.bind_tools(tools)

# Build agent graph with tool calling
```

### Human-in-the-Loop
```python
from langgraph.types import interrupt

def human_approval(state):
    decision = interrupt("Approve this action?")
    return {"approved": decision}

# Graph with human intervention
```

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

### Development Setup

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🌟 Resources

### Official Documentation
- [LangGraph Documentation](https://langchain-ai.github.io/langgraph/)
- [LangChain Documentation](https://python.langchain.com/)
- [OpenAI API Reference](https://platform.openai.com/docs)

### Community Resources
- [LangGraph GitHub](https://github.com/langchain-ai/langgraph)
- [LangChain GitHub](https://github.com/langchain-ai/langchain)
- [Discord Community](https://discord.gg/langchain)

### Related Projects
- [LangSmith](https://smith.langchain.com/) - Monitoring and debugging
- [LangServe](https://langchain-ai.github.io/langserve/) - Serving LangChain applications

---

**Happy Learning! 🚀**

If you find this tutorial helpful, please give it a ⭐ on GitHub!