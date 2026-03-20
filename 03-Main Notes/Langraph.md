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

[Building AI Agents with Open Source Frameworks](https://www.coursera.org/learn/agentic-ai-with-langgraph-crewai-autogen-and-beeai/lecture/GE6RG/building-ai-agents-with-open-source-frameworks?trk_ref=coach_copy)  Mar 20, 2026

This video lecture focuses on building AI agents using various open-source frameworks, highlighting their structures and functionalities.

Agentic Frameworks Overview

- Introduces frameworks like Crue AI, LangGraph, Autogen, and BAI for creating multi-agent workflows.
- Discusses the concept of agentic AI, which involves autonomous systems capable of thinking, planning, and acting.

Crue AI and LangGraph

- Crue AI allows for role-based team simulations, where agents are defined with specific roles and tasks, executing them collaboratively.
- LangGraph offers fine-grained control over workflows using directed acyclic graphs (DAGs), enabling complex interactions and structured automation.

Autogen and BAI Frameworks

- Autogen facilitates dialogue-driven interactions among agents, ideal for conversational applications and quick prototyping.
- BAI supports modular workflows with tool integration, allowing agents to work in parallel or sequentially to achieve specific goals.
  
  
  #### Coach

Understanding State in LangGraph: A Beginner's Guide

In LangGraph, "state" refers to a collection of variables that hold information about the current context of a workflow. Think of it as a digital notepad where you jot down important details that help guide the process. This state allows different parts of your program to share and access information, making it easier to manage complex tasks.

Imagine you're organizing a big event, like a wedding. The state would be like your checklist, containing details such as the guest list, menu options, and schedule. As you receive new requests or changes, you update this checklist. Similarly, in LangGraph, the state keeps track of essential data, like meal requests or dish details, which can be accessed and modified by different components of your workflow. This ensures that everyone involved in the process is on the same page and can work together efficiently.

Is there any other concept within the content that you need an explanation for?

And if you want to continue exploring this topic, try one of these follow-up questions:

Play

00:00

00:00

Mute

Settings

# Cheat Sheet: Agentic Frameworks and Design Patterns for Effective AI Systems

**Estimated time:** 20 minutes

---

## 1. Agentic AI Design Patterns

**Agentic design patterns** are reusable strategies for organizing multiple language model "agents" into structured workflows. These agents collaborate—each with specialized roles—to handle complex tasks that go beyond what a single prompt can manage. These patterns improve clarity, scalability, and control in LLM-powered applications. They are used to decompose complex problems into smaller, specialized tasks and add structure and memory to multi-step reasoning or decision flows.

### 1.1 Fundamental Components

- **Agent**: a specialized LLM prompt + logic unit
- **Orchestrator**: routes inputs, maintains state, aggregates outputs
- **Worker**: executes a single responsibility (for example, summarization, translation)
- **Router**: dispatches tasks based on intent or condition
- **Evaluator**: inspects and scores outputs for quality or correctness

These components embody the principle of separation of concerns. Decomposing your workflow into distinct agent roles makes it easier to debug, test, and reuse logic. It mirrors real-world software architecture by assigning specialized responsibilities to each part of the system.

### 1.2 Core Patterns

|Pattern|Description|Use Cases|
|---|---|---|
|**Orchestration**|Central controller coordinates agents and tracks state|Document pipelines, decision trees, role-based workflows|
|**Reflection**|Evaluate and refine outputs with internal feedback loops|Quality improvement, self-correction, iterative generation|
|**Sequential Coordination**|Chain agents in a fixed order|Multi‑step data pipelines (ingest → summarize → refine)|
|**Intent‑Based Routing**|Dispatch inputs to agents based on user intent/class.|Multi‑domain assistants (finance vs. weather vs. chat)|
|**Parallel Execution**|Fan‑out tasks to multiple agents concurrently|Batch translations, multi‑hypothesis generation|
|**Prompt Chaining**|Decompose a complex prompt into a sequence of simpler prompts|Complex content creation (outline → draft → edit)|

> While "agentic frameworks" can include a variety of libraries and platforms (e.g., LangChain, AutoGen), this reading focuses exclusively on LangGraph as the agentic framework. All examples, patterns, and code snippets use LangGraph's APIs and conventions to illustrate core design patterns for building effective, multi‑agent AI workflows.

---

## 2. LangGraph Workflows

### 2.1 Agents with Structured Output

First, we need chains of LLMs and prompts that configure agents to perform specific tasks. These agents will later be used in workers to perform certain tasks in the workflow. It's important that these agents have structured outputs so they return data in our desired format. This ensures that **LangGraph workflows** remain reliable and composable, especially when downstream agents depend on the outputs of earlier ones.

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
18. 18
19. 19
20. 20
21. 21
22. 22
23. 23
24. 24
25. 25
26. 26

27. `from pydantic import BaseModel, Field`
28. `from langchain_openai import ChatOpenAI`
29. `from langchain_core.prompts import ChatPromptTemplate`

30. `# instantiate LLM`
31. `llm = ChatOpenAI(model="gpt-4o-mini")`

32. `# define output schema`
33. `class Output(BaseModel):`
34.     `name: str = Field(`
35.         `description="Name of the structured output"`
36.     `)`
37.     `field: str = Field(`
38.         `description="Field of the structured output"`
39.     `)`

40. `# create the LLM prompt template`
41. `prompt = ChatPromptTemplate.from_messages([`
42.     `(`
43.         `"human/system",`
44.         `"Prompt with {input}"`
45.     `)`
46. `])`

47. `# use LCEL to pipe the prompt to the LLM and pass in the structured output schema`
48. `pipe = prompt | llm.with_structured_output(Output)`

Copied!Wrap Toggled!

### 2.2 States

A simple typed dictionary that tracks variables, values and states across a workflow. This state is what gets upated across a LangGraph `StateGraph` workflow so the **field names** and **data types** are **important**.

1. 1
2. 2
3. 3
4. 4
5. 5
6. 6

7. `class State(TypedDict):`
8.     `string_field: str`
9.     `string_list_field: List[str]`
10.     `int_field: int`
11.     `input_field: str`
12.     `output_field: Output`

Copied!Wrap Toggled!

In LangGraph, the state serves as a contract between nodes. It defines the schema for what data is expected, produced, and passed between components. This contract enables better debugging, validation, and scalability. It also ensures agents interact through a shared vocabulary, reducing unexpected type mismatches and silent failures.

### 2.3 Worker Nodes

These are functions that make up the graph and execute certain tasks with the provided input data. They return an update to the persistent state across a `StateGraph`, updating field(s) with the new data.

1. 1
2. 2
3. 3
4. 4
5. 5
6. 6
7. 7
8. 8

9. `def worker(state: State):`
10.      `"""Worker that generates the pipe to fill in the output_field of a state"""`

11.     `# use the pipe LLM to generate an Output`
12.     `output = pipe.invoke({"input": state["input_field"]})`

13.     `# return the Output object as a dictionary to update the state`
14.     `return {"output_field": output}`

Copied!Wrap Toggled!

### 2.4 Building the Workflow

|Component|What It Does|How to Add It|
|---|---|---|
|**Node**|Encapsulates a function (agent/tool) that processes input and returns output|`graph.add_node("name", fn)` or `Node("name", func=fn)`|
|**Edge**|Defines a direct connection between two nodes|`graph.add_edge("from_node", "to_node")`|
|**Conditional Edge**|Routes execution based on a boolean or value-based condition|`graph.add_conditional_edges("node", {"True": "A", "False": "B"})`|
|**Entry Point**|Designates where the graph starts execution|`graph.set_entry_point("start_node")` or `graph.add_edge(START, "to_first_node")`|
|**End Point**|Designates a terminal node where execution finishes|`graph.set_finish_point("end_node")` or `graph.add_edge("last_node", END)`|
|**Parallel Branch**|Runs multiple nodes concurrently, gathers all results|`graph.add_parallel("parent", ["node1", "node2"])`|
|**State**|Stores and passes shared context across the graph|Passed automatically between nodes via input/output dicts|

- First initialize the `StateGraph` and pass in the `State` variable that will be tracked across the workflow.
- Then add the nodes to the graph giving them labels.
- Then add the edges to the graph connectin the nodes in your desired order.
- Lastly compile the workflow and invoke it with an input.

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

18. `from langgraph.graph import StateGraph, END, START`

19. `# initialize the graph`
20. `builder = StateGraph(State)`

21. `# add the nodes`
22. `builder.add_node("worker", worker)`

23. `# add the edges`
24. `builder.add_edge(START, "worker")`
25. `builder.add_edge("worker", END)`

26. `# compile the workflow into an executable`
27. `workflow = builder.compile()`

28. `# invoke the workflow with an example input`
29. `workflow.invoke({"input": "Example input"})`

Copied!Wrap Toggled!

### 2.5 Workflow Visualization

Visualizing LangGraph graphs is easy in a JupyterLab environment. It helps you quickly understand the flow of logic between nodes—especially in more complex graphs involving loops, branching, or multiple agents.

If you're working in a notebook, you can generate and display the graph using Mermaid syntax or as an image.

**Mermaid Chart Visualization (Jupyter-friendly)**

If your `StateGraph` object supports it (ex. `workflow.get_graph()`), you can render it using Mermaid diagrams:

1. 1
2. 2
3. 3
4. 4

5. `from IPython.display import Image, display`

6. `# display the orchestrator workflow as a Mermaid-rendered PNG`
7. `display(Image(orchestrator_worker.get_graph().draw_mermaid_png()))`

Copied!Wrap Toggled!

## 3. Orchestrator–Worker Pattern

An industry-tested coordination pattern used to break down complex workflows into modular, repeatable tasks. An orchestrator delegates responsibilities to specialized worker agents and aggregates their outputs to form a cohesive result. This pattern improves maintainability, allows for dynamic control flow, and supports multi-stage pipelines with clear structure and logic.

![orchestration](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/Ylv-0mjQHTekX59nJObTVg/orchestration.png)  

|Component|Purpose|
|---|---|
|**Orchestrator Node**|Central control unit that routes data, manages logic, and delegates tasks|
|**Worker Node**|Executes a single, focused subtask within the larger workflow|
|**Routing Logic**|Decides which worker(s) to activate based on input or intermediate state|
|**Dynamic Edges**|Connect orchestrator to multiple workers depending on routing conditions|

---

## 4. Reflection Pattern

A self-improving feedback pattern that allows agents to evaluate, critique, and revise their outputs iteratively. By looping results through an evaluator node and back into the generator, this pattern enables internal quality control, self-correction, and optimization, making it ideal for high-stakes tasks requiring accuracy, consistency, or refinement over time.

![reflection](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/sbdKL2dYTuJ6RcPomfG_mQ/reflection.png)  

|Component|Purpose|
|---|---|
|**Generator Node**|Generates initial output and generates further outputs when feedback is available|
|**Evaluator Node**|Scores agent outputs (correctness, style, etc.)|
|**Routing Node**|Re‑routes based on evaluator feedback, is added as a conditional edge because it might lead to END or loop back to the Generator Node|
|**Testing Node**|Unit‑tests chains with known in/out examples|

## Summary

This cheat sheet gives you a practical foundation for applying agentic design patterns using **LangGraph**. By mastering these core patterns and components, you'll be equipped to structure **complex LLM workflows**, enhance reliability through **state management**, and confidently prototype or scale intelligent systems. Use it as a quick **reference** when designing, debugging, or extending your own multi-agent applications.

## Author