[Core Components of LangGraph](https://www.coursera.org/learn/agentic-ai-with-langchain-and-langgraph/lecture/ius5N/core-components-of-langgraph?trk_ref=coach_copy)  Mar 19, 2026

This video lecture focuses on the core components of LangGraph, an advanced framework for building stateful, multi-agent applications within the LangChain ecosystem.

Core Components of LangGraph

- **Nodes and Edges**: Nodes represent individual steps or functions that perform computations, while edges define the execution flow between these nodes.
- **State Management**: A shared memory structure that retains context across nodes, allowing workflows to maintain continuity.

Unique Capabilities of LangGraph

- **Dynamic Decision-Making**: Supports looping and branching, enabling agents to make real-time decisions based on context.
- **Human-in-the-Loop Functionality**: Allows for manual intervention during execution, enhancing adaptability.

Advantages Over Traditional Programming

- **Explicit State Management**: Unlike linear programming constructs, LangGraph allows for complex workflows with conditional transitions and modularity.
- **Enhanced Observability**: Provides insights into the execution path, aiding in debugging and monitoring.

Visualization and Practical Application

- **Mermaid Diagrams**: LangGraph workflows can be visualized, making it easier to understand and debug complex structures.
- **Real-World Example**: Demonstrates how LangGraph can be used to build a customer support agent that retains conversational memory, unlike traditional loops.
  
  Effective LangGraph architecture focuses on simplicity, clarity, and modularity:

- Begin simply and incrementally add complexity.
- Keep state structures explicit and manageable.
- Design independent, clearly defined nodes.
- Proactively handle potential errors.
  
  **Comparison of LangChain and LangGraph**

- LangChain focuses on sequential tasks and uses a directed acyclic graph (DAG) structure, while LangGraph supports more complex interactions with loops and state management.
- LangChain has limited state management capabilities, whereas LangGraph allows all nodes to access and modify state, enabling more context-aware behaviors.
- Use cases for LangChain include sequential tasks, while LangGraph excels in scenarios requiring ongoing interaction and adaptation, such as virtual assistants.
  
  [The Art of AI Self-Improvement: Building Reflection Agents](https://www.coursera.org/learn/agentic-ai-with-langchain-and-langgraph/lecture/XrU3z/the-art-of-ai-self-improvement-building-reflection-agents?trk_ref=coach_copy)  Mar 20, 2026

This video lecture focuses on the concept of basic reflection agents and their role in improving AI outputs through iterative self-correction.

**Understanding Reflection Agents**

- Reflection agents analyze their performance and enhance strategies through a feedback loop.
- They consist of a generator that produces content and a reflector that critiques it.

**Building a Reflection Agent**

- The process involves setting up generator and reflector roles to refine outputs iteratively.
- An example illustrates how a generator suggests ideas (e.g., "Wear a fedora") while the reflector critiques them, leading to improved responses.

**Implementing with LangChain and LangGraph**

- The lecture covers how to use LangChain for generating and critiquing content, and LangGraph for managing conversation context.
- It details the construction of a workflow that includes nodes for generation and reflection, ensuring continuous improvement of AI-generated content.
  
  ## Why JSON-Serializable Pydantic Models Are Powerful

|Feature|Benefit|
|---|---|
|Type Validation|Ensures inputs and outputs conform to expected schema|
|Reusability|Use base classes such as `TwoOperands` across multiple tools|
|JSON Serialization|`.json()` and `.parse_raw()` simplify tool chaining and I/O|
|Extensibility|Easily add more tools (e.g., multiply, divide)|

---

## Final Thoughts and Alternatives

Using Pydantic models to define JSON-serializable tool inputs and outputs makes your LLM applications:

- Robust and error-proof.
- Compatible with orchestration frameworks such as LangChain, CrewAI, Watsonx, and so on.
- Easy to test, maintain, and extend.

This forms the foundation of building reliable, multi-tool LLM agents.

---

### Optional Note: Pydantic vs. Python Dataclasses

You **don't need** to use Pydantic exclusively. Since Python 3.7, `dataclasses` offer a lightweight alternative for defining data models with built-in parsing and serialization. However, Pydantic provides more advanced features such as:

- Validators for complex constraints
- Extra configuration options
- Better integration with libraries like LangChain and FastAPI

Pydantic is generally recommended due to its maturity and feature set, and it's the default choice in popular frameworks.


[Understanding Reflexion Agents](https://www.coursera.org/learn/agentic-ai-with-langchain-and-langgraph/lecture/SPJOd/understanding-reflexion-agents?trk_ref=coach_copy)  Mar 20, 2026

This video lecture focuses on understanding Reflexion agents and their role in enhancing AI responses through iterative self-critique and tool use.

Reflexion Agents Overview

- Reflexion agents build on reflection agents by continuously improving responses through self-critiques and external tools.
- They produce outputs with citations and current information, enhancing the reliability of their responses.

Reflection Process

- The process involves a cycle of generation, critique, and revision, which improves clarity, accuracy, and usefulness.
- A query initiates a back-and-forth process until a satisfactory response is generated, incorporating real-time data when necessary.

Iterative Improvement

- Reflexion agents can identify and rectify their weaknesses, learning from past outputs to enhance future responses.
- They utilize structured schema-based outputs to clearly differentiate between components like responses, critiques, and tool queries, ensuring clarity in communication.
  
  ## Cheat Sheet: Multi-Agent Systems and Agentic RAG with LangGraph

### Why multi-agent systems?

|Challenge faced by single LLM agents|Multi-agent system solution|
|---|---|
|Context overload|Splits tasks among agents to reduce burden|
|Role confusion|Agents specialize in distinct cognitive roles|
|Debugging difficulty|Modular agents ease error tracing|
|Quality dilution|Each agent excels at a focused subtask|

---

### Typical multi-agent communication patterns

|Pattern|Description|Example|
|---|---|---|
|**Sequential (Pipeline)**|Agents work one after another, passing results|Research → Analysis → Writing → Review|
|**Parallel with aggregation**|Multiple agents run concurrently, results combined|SEO analysis, fact-checking, writing run in parallel|
|**Interactive dialogue**|Agents exchange messages to clarify or refine|Requirements agent queries data agent before finalizing|

---

### Real-world multi-agent use cases

|Use case|Agents & workflow|Benefit|
|---|---|---|
|Automated market report|Research → Data analysis → Writing → Critique → Editing|Faster, accurate, well-rounded reports|
|Customer support|Intent detection → Knowledge retrieval → Response → Escalation|Dynamic, personalized, scalable responses|
|Legal contract review|Clause extraction → Compliance check → Risk analysis → Summary|Thorough, accurate, actionable legal reviews|

---

### Communication protocols

- **Model Context Protocol (MCP):** JSON-RPC-based interface for LLMs to interact with external tools/services, enabling modular, real-time collaboration.
- **IBM Agent Communication Protocol (ACP):** Standardizes message exchange among autonomous agents for secure, scalable enterprise workflows.

---

### Frameworks supporting multi-agent LLM systems

|Framework|Focus/Features|
|---|---|
|**LangGraph**|Graph-based orchestration, shared state, dynamic routing|
|**AutoGen**|Agent self-organization, negotiation, adaptive collaboration|
|**CrewAI**|Structured workflows, strict typed interfaces (Pydantic), high-fidelity data passing|
|**BeeAI**|Enterprise-grade modular orchestration, uses IBM ACP|

---

### LangGraph multi-agent workflow essentials

### Core concepts

- **Directed graph nodes:** represent agents/tasks
- **Edges:** control flow between agents
- **Shared state:** a TypedDict or similar, passed and updated by all agents
- **Routing logic:** dynamically determines the next agent based on the state

---

### Example of shared state definition

1. 1
2. 2
3. 3
4. 4
5. 5
6. 6
7. 7
8. 8
9. 9
10. 10

11. `from typing import TypedDict, Optional, List`

12. `class SalesReportState(TypedDict):`
13.     `request: str`
14.     `raw_data: Optional[dict]`
15.     `processed_data: Optional[dict]`
16.     `chart_config: Optional[dict]`
17.     `report: Optional[str]`
18.     `errors: List[str]`
19.     `next_action: str`

Copied!Wrap Toggled!

---

### Example of agent node skeleton

1. 1
2. 2
3. 3
4. 4
5. 5

6. `def data_collector_agent(state: SalesReportState) -> SalesReportState:`
7.     `# Collect raw data based on state['request']`
8.     `state['raw_data'] = {...}`
9.     `state['next_action'] = 'process'`
10.     `return state`

Copied!Wrap Toggled!

Repeat for other agents: `data_processor_agent`, `chart_generator_agent`, `report_generator_agent`, `error_handler_agent`.

---

### Example of routing function

1. 1
2. 2
3. 3
4. 4
5. 5
6. 6
7. 7
8. 8
9. 9
10. 10

11. `def route_next_step(state: SalesReportState) -> str:`
12.     `routing = {`
13.         `"collect": "data_collector",`
14.         `"process": "data_processor",`
15.         `"visualize": "chart_generator",`
16.         `"report": "report_generator",`
17.         `"error": "error_handler",`
18.         `"complete": "END"`
19.     `}`
20.     `return routing.get(state.get("next_action", "collect"), "END")`

Copied!Wrap Toggled!

---

### Building the workflow graph

1. 1
2. 2
3. 3
4. 4
5. 5
6. 6
7. 7
8. 8
9. 9
10. 10
11. 11
12. 12
13. 13
14. 14
15. 15
16. 16
17. 17

18. `from langgraph.graph import StateGraph, END`

19. `def create_workflow():`
20.     `workflow = StateGraph(SalesReportState)`

21.     `workflow.add_node("data_collector", data_collector_agent)`
22.     `workflow.add_node("data_processor", data_processor_agent)`
23.     `workflow.add_node("chart_generator", chart_generator_agent)`
24.     `workflow.add_node("report_generator", report_generator_agent)`
25.     `workflow.add_node("error_handler", error_handler_agent)`

26.     `# Define conditional edges based on routing decisions`
27.     `workflow.add_conditional_edges("data_collector", route_next_step, {...})`
28.     `# Repeat for other nodes...`

29.     `workflow.set_entry_point("data_collector")`
30.     `return workflow.compile()`

Copied!Wrap Toggled!

---

### Running the workflow

1. 1
2. 2
3. 3
4. 4
5. 5
6. 6
7. 7
8. 8
9. 9
10. 10
11. 11
12. 12
13. 13

14. `def run_workflow():`
15.     `app = create_workflow()`
16.     `initial_state = SalesReportState(`
17.         `request="Q1-Q2 Sales Report",`
18.         `raw_data=None,`
19.         `processed_data=None,`
20.         `chart_config=None,`
21.         `report=None,`
22.         `errors=[],`
23.         `next_action="collect"`
24.     `)`
25.     `final_state = app.invoke(initial_state)`
26.     `return final_state`

Copied!Wrap Toggled!

---

### Agentic RAG systems

- Combine **Retrieval**, **Reasoning**, and **Verification** using specialized agents
- Retrieval agent fetches relevant knowledge/data
- Reasoning agent performs inference and decision-making
- Verification agent checks results for accuracy and consistency
- Multi-agent design improves reliability and trustworthiness

---

## Best practices & challenges

|Challenge|Strategy|
|---|---|
|Context management|Share only relevant info, avoid overload|
|Granularity|Balance agent count — not too few or too many|
|Communication cost|Optimize message size and frequency|
|Error handling|Implement fallback, retries, and error agents|

---

## Author