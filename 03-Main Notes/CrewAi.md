[Design AI Agent Workflows with CrewAI](https://www.coursera.org/learn/agentic-ai-with-langgraph-crewai-autogen-and-beeai/lecture/1OLhV/design-ai-agent-workflows-with-crewai?trk_ref=coach_copy)  Mar 20, 2026

This video lecture focuses on the core components of a Crue AI system and how to design AI agent workflows effectively.

Core Concepts of Crue AI

- **Task Definition**: A task acts as a director, specifying the goal and the agent responsible for achieving it. For example, creating a 30-second car commercial.
- **Agent Characteristics**: Agents are AI entities defined by structured prompts, including their role, goal, and backstory, which guide their actions and personality.

Workflow Execution

- **Sequential Task Execution**: Tasks can be executed in a linear order, where the output of one task serves as the input for the next, allowing for a feedback loop.
- **Crew Object**: This object integrates agents, tasks, tools, and execution flow into a cohesive system, enabling multi-agent collaboration.

Output and Evaluation

- **Crew Output Object**: After task completion, results are compiled into a crew output object, which includes raw outputs, individual task results, and token usage for performance tracking.
  
  # Reading: Structured Outputs in CrewAI

**Estimated time:** 6 minutes

## Objectives

After completing this reading, you will be able to:

- Explain the importance of structured outputs in AI workflows
- Explain the use of Pydantic to enable structured outputs
- List the key features of Pydantic in the context of structured outputs
- Explore how structured outputs are implemented in CrewAI
- List the benefits of using structured outputs in CrewAI

## Why structured outputs matter in AI workflows

How outputs are structured plays a critical role in AI applications, especially those with multiple agents or complex data. Free-form text from language models can be difficult to parse, prone to ambiguity, and risky for downstream tasks. On the other hand, structured outputs (like JSON or objects with defined fields) ensure consistency and make data easier to extract and use.

CrewAI helps developers enforce structured outputs by letting them define schemas for task responses, which leads to more reliable and predictable outcomes. In multi-agent workflows, this structure ensures that one agent's output can be cleanly interpreted by the next, thus reducing miscommunication, data loss, and hallucinations. The result is smoother agent collaboration and easier system integration.

---

## Introduction to Pydantic for data modeling

To enable structured outputs, CrewAI primarily leverages a powerful Python library called [Pydantic](https://docs.pydantic.dev/latest/). Pydantic is commonly used for data validation and settings management by defining data models in Python. A Pydantic model is essentially a class that inherits from [BaseModel](https://docs.pydantic.dev/latest/api/base_model/) and defines a set of fields with types.

When you create an instance of this model, Pydantic automatically checks that any data you pass in matches the expected types (and even converts types when possible). If the data is missing required fields or has the wrong type, Pydantic will raise a validation error, alerting you to the mismatch.

## Key features of Pydantic

Here are some of the key features of Pydantic:

|Feature|Description|
|---|---|
|**Data validation**|Ensures inputs match expected types. If a field expects an integer but receives a string, Pydantic will raise an error.<br><br>1. 1<br>2. 2<br>3. 3<br>4. 4<br>5. 5<br>6. 6<br><br>1. `from pydantic import BaseModel`<br><br>3. `class Person(BaseModel):`<br>4.     `age: int`<br><br>6. `Person(age="twenty")  # Raises ValidationError`<br><br>Copied!Wrap Toggled!|
|**Automatic type conversion**|Pydantic attempts to coerce inputs into the expected type when possible.<br><br>1. 1<br>2. 2<br>3. 3<br>4. 4<br>5. 5<br>6. 6<br>7. 7<br>8. 8<br><br>1. `from datetime import date`<br>2. `from pydantic import BaseModel`<br><br>4. `class Event(BaseModel):`<br>5.     `date: date`<br><br>7. `e = Event(date="2025-07-24")`<br>8. `print(e.date)  # Outputs: 2025-07-24`<br><br>Copied!Wrap Toggled!|
|**Nested models and complex types**|Models can include other models, lists, and optional fields. This is ideal for structured data like JSON.<br><br>1. 1<br>2. 2<br>3. 3<br>4. 4<br>5. 5<br>6. 6<br>7. 7<br>8. 8<br>9. 9<br>10. 10<br><br>1. `from typing import List`<br>2. `from pydantic import BaseModel`<br><br>4. `class Item(BaseModel):`<br>5.     `name: str`<br><br>7. `class Cart(BaseModel):`<br>8.     `items: List[Item]`<br><br>10. `cart = Cart(items=[{"name": "Apple"}])`<br><br>Copied!Wrap Toggled!|
|**Easy serialization**|Convert models to dictionaries or JSON strings for storage or API responses.<br><br>1. 1<br>2. 2<br>3. 3<br><br>1. `user = Person(age=30)`<br>2. `print(user.dict())   # {'age': 30}`<br>3. `print(user.json())   # '{"age": 30}'`<br><br>Copied!Wrap Toggled!|

---

## Implementing structured output in a CrewAI task

Let us see how we can actually use Pydantic with CrewAI to get structured outputs:

|Concept|Explanation|
|---|---|
|**Define a Pydantic model**|Start by defining what data your task should return. Create a class that inherits from `BaseModel` and specify typed fields:<br><br>1. 1<br>2. 2<br>3. 3<br>4. 4<br>5. 5<br><br>1. `from pydantic import BaseModel`<br><br>3. `class BlogSummary(BaseModel):`<br>4.     `title: str`<br>5.     `content: str`<br><br>Copied!Wrap Toggled!<br><br>This model enforces a schema with two required fields: `title` and `content`. You can also nest models or use lists and dicts for more complex structures.|
|**Nested Pydantic models**|You can define a model that contains other models. This is useful when your output has grouped or hierarchical data.<br><br>1. 1<br>2. 2<br>3. 3<br>4. 4<br>5. 5<br>6. 6<br>7. 7<br>8. 8<br>9. 9<br>10. 10<br><br>1. `from typing import List`<br>2. `from pydantic import BaseModel`<br><br>4. `class Ingredient(BaseModel):`<br>5.     `name: str`<br>6.     `quantity: str`<br><br>8. `class MealPlan(BaseModel):`<br>9.     `meal_name: str`<br>10.     `ingredients: List[Ingredient]`<br><br>Copied!Wrap Toggled!<br><br>This lets you represent nested data, such as a list of ingredients inside a meal plan. CrewAI will validate every field inside each nested model automatically.|
|**Attach model to task**|In your CrewAI task, use the `output_pydantic` (or `output_json`) parameter to bind the model. This enforces structured output:<br><br>1. 1<br>2. 2<br>3. 3<br>4. 4<br>5. 5<br>6. 6<br><br>1. `blog_task = Task(`<br>2.     `description="Generate a catchy blog title and a short content about a topic.",`<br>3.     `expected_output="A JSON object with 'title' and 'content' fields.",`<br>4.     `agent=blog_agent,`<br>5.     `output_pydantic=BlogSummary`<br>6. `)`<br><br>Copied!Wrap Toggled!<br><br>Use `output_pydantic` if you want the output as a Pydantic object, or `output_json` if you prefer a plain Python dict.|
|**Using YAML with Pydantic**|While you can't reference Pydantic classes directly in YAML, you can define task configurations in YAML and attach the model in Python using `CrewBase`:<br><br>1. 1<br>2. 2<br>3. 3<br>4. 4<br>5. 5<br>6. 6<br><br>1. `@task`<br>2. `def blog_task(self) -> Task:`<br>3.     `return Task(`<br>4.         `config=self.tasks_config['blog_task'],  # From YAML`<br>5.         `output_json=BlogSummary                 # Defined in Python`<br>6.     `)`<br><br>Copied!Wrap Toggled!<br><br>This approach combines YAML's ease of editing with Python's strict schema enforcement.|
|**Run the crew**|Execute the crew as usual using `crew.kickoff()`. The returned result includes structured data:<br><br>- `result.raw`: Raw model output<br>- `result.json_dict`: Dict output (if using `output_json`)<br>- `result.pydantic`: Pydantic object (if using `output_pydantic`)<br><br>You can also use dictionary-like access with `result["title"]` due to implemented `**getitem**` support.|
|**Use the structured data**|With structured output, you can cleanly feed data into downstream systems, pass it to other tasks, or serialize it:<br><br>1. 1<br>2. 2<br><br>1. `title = result.pydantic.title  # if using output_pydantic`<br>2. `title = result.json_dict.get("title")  # if using output_json`<br><br>Copied!Wrap Toggled!<br><br>This makes AI output a reliable part of your program’s data pipeline—no parsing or guesswork required.|

---

## Why structured output matters in CrewAI

Now that we've seen how to define and apply Pydantic models in CrewAI, it's important to understand why this practice is so valuable in real-world workflows. The following table outlines the practical benefits of using structured outputs—not just in theory, but in how they help CrewAI applications become more robust, maintainable, and production-ready.

|Benefit|How it helps in CrewAI workflows|
|---|---|
|**Type safety and validation**|CrewAI validates the LLM output against the schema you define. If the model returns incorrect types or misses required fields, you're immediately notified. This prevents subtle bugs from creeping into your pipeline.|
|**Clear data contracts**|A Pydantic model acts like a formal agreement: "This task will always return these fields, with these types." This makes the codebase easier to understand, especially in collaborative projects where agents and tasks are reused.|
|**System integration**|Whether you're pushing the output to an API, saving it to a database, or displaying it in a UI, structured outputs make integration seamless. There's no need to manually parse or clean the LLM response.|
|**Less post-processing**|Without structured outputs, developers often write custom parsing or regex logic to extract information from raw text. With CrewAI and Pydantic, the heavy lifting is handled for you—validated, parsed, and ready to use.|
|**Consistent agent handoffs**|In multi-agent workflows, structure ensures smooth transitions. One agent's output becomes the next agent's input, without ambiguity. This avoids hallucinated formats or misinterpretation between agents.|
|**LLM behavior alignment**|When LLMs are prompted to follow a structured schema (e.g., "Return a JSON with fields A, B, and C"), they are more likely to stay focused and accurate. It works like soft prompting or function-calling—constraining the model's output space.|

## Summary

Structured outputs in CrewAI let you combine the flexibility of language models with the reliability of defined data formats. By using Pydantic models, you create a clear structure that CrewAI enforces, making outputs easier to validate, reuse, and integrate. This approach helps you build more reliable workflows, connect multiple agents smoothly, and plug AI results directly into real systems. It's a key step in turning experimental AI into production-ready applications.# Reading: Structured Outputs in CrewAI

**Estimated time:** 6 minutes

## Objectives

After completing this reading, you will be able to:

- Explain the importance of structured outputs in AI workflows
- Explain the use of Pydantic to enable structured outputs
- List the key features of Pydantic in the context of structured outputs
- Explore how structured outputs are implemented in CrewAI
- List the benefits of using structured outputs in CrewAI

## Why structured outputs matter in AI workflows

How outputs are structured plays a critical role in AI applications, especially those with multiple agents or complex data. Free-form text from language models can be difficult to parse, prone to ambiguity, and risky for downstream tasks. On the other hand, structured outputs (like JSON or objects with defined fields) ensure consistency and make data easier to extract and use.

CrewAI helps developers enforce structured outputs by letting them define schemas for task responses, which leads to more reliable and predictable outcomes. In multi-agent workflows, this structure ensures that one agent's output can be cleanly interpreted by the next, thus reducing miscommunication, data loss, and hallucinations. The result is smoother agent collaboration and easier system integration.

---

## Introduction to Pydantic for data modeling

To enable structured outputs, CrewAI primarily leverages a powerful Python library called [Pydantic](https://docs.pydantic.dev/latest/). Pydantic is commonly used for data validation and settings management by defining data models in Python. A Pydantic model is essentially a class that inherits from [BaseModel](https://docs.pydantic.dev/latest/api/base_model/) and defines a set of fields with types.

When you create an instance of this model, Pydantic automatically checks that any data you pass in matches the expected types (and even converts types when possible). If the data is missing required fields or has the wrong type, Pydantic will raise a validation error, alerting you to the mismatch.

## Key features of Pydantic

Here are some of the key features of Pydantic:

|Feature|Description|
|---|---|
|**Data validation**|Ensures inputs match expected types. If a field expects an integer but receives a string, Pydantic will raise an error.<br><br>1. 1<br>2. 2<br>3. 3<br>4. 4<br>5. 5<br>6. 6<br><br>1. `from pydantic import BaseModel`<br><br>3. `class Person(BaseModel):`<br>4.     `age: int`<br><br>6. `Person(age="twenty")  # Raises ValidationError`<br><br>Copied!Wrap Toggled!|
|**Automatic type conversion**|Pydantic attempts to coerce inputs into the expected type when possible.<br><br>1. 1<br>2. 2<br>3. 3<br>4. 4<br>5. 5<br>6. 6<br>7. 7<br>8. 8<br><br>1. `from datetime import date`<br>2. `from pydantic import BaseModel`<br><br>4. `class Event(BaseModel):`<br>5.     `date: date`<br><br>7. `e = Event(date="2025-07-24")`<br>8. `print(e.date)  # Outputs: 2025-07-24`<br><br>Copied!Wrap Toggled!|
|**Nested models and complex types**|Models can include other models, lists, and optional fields. This is ideal for structured data like JSON.<br><br>1. 1<br>2. 2<br>3. 3<br>4. 4<br>5. 5<br>6. 6<br>7. 7<br>8. 8<br>9. 9<br>10. 10<br><br>1. `from typing import List`<br>2. `from pydantic import BaseModel`<br><br>4. `class Item(BaseModel):`<br>5.     `name: str`<br><br>7. `class Cart(BaseModel):`<br>8.     `items: List[Item]`<br><br>10. `cart = Cart(items=[{"name": "Apple"}])`<br><br>Copied!Wrap Toggled!|
|**Easy serialization**|Convert models to dictionaries or JSON strings for storage or API responses.<br><br>1. 1<br>2. 2<br>3. 3<br><br>1. `user = Person(age=30)`<br>2. `print(user.dict())   # {'age': 30}`<br>3. `print(user.json())   # '{"age": 30}'`<br><br>Copied!Wrap Toggled!|

---

## Implementing structured output in a CrewAI task

Let us see how we can actually use Pydantic with CrewAI to get structured outputs:

|Concept|Explanation|
|---|---|
|**Define a Pydantic model**|Start by defining what data your task should return. Create a class that inherits from `BaseModel` and specify typed fields:<br><br>1. 1<br>2. 2<br>3. 3<br>4. 4<br>5. 5<br><br>1. `from pydantic import BaseModel`<br><br>3. `class BlogSummary(BaseModel):`<br>4.     `title: str`<br>5.     `content: str`<br><br>Copied!Wrap Toggled!<br><br>This model enforces a schema with two required fields: `title` and `content`. You can also nest models or use lists and dicts for more complex structures.|
|**Nested Pydantic models**|You can define a model that contains other models. This is useful when your output has grouped or hierarchical data.<br><br>1. 1<br>2. 2<br>3. 3<br>4. 4<br>5. 5<br>6. 6<br>7. 7<br>8. 8<br>9. 9<br>10. 10<br><br>1. `from typing import List`<br>2. `from pydantic import BaseModel`<br><br>4. `class Ingredient(BaseModel):`<br>5.     `name: str`<br>6.     `quantity: str`<br><br>8. `class MealPlan(BaseModel):`<br>9.     `meal_name: str`<br>10.     `ingredients: List[Ingredient]`<br><br>Copied!Wrap Toggled!<br><br>This lets you represent nested data, such as a list of ingredients inside a meal plan. CrewAI will validate every field inside each nested model automatically.|
|**Attach model to task**|In your CrewAI task, use the `output_pydantic` (or `output_json`) parameter to bind the model. This enforces structured output:<br><br>1. 1<br>2. 2<br>3. 3<br>4. 4<br>5. 5<br>6. 6<br><br>1. `blog_task = Task(`<br>2.     `description="Generate a catchy blog title and a short content about a topic.",`<br>3.     `expected_output="A JSON object with 'title' and 'content' fields.",`<br>4.     `agent=blog_agent,`<br>5.     `output_pydantic=BlogSummary`<br>6. `)`<br><br>Copied!Wrap Toggled!<br><br>Use `output_pydantic` if you want the output as a Pydantic object, or `output_json` if you prefer a plain Python dict.|
|**Using YAML with Pydantic**|While you can't reference Pydantic classes directly in YAML, you can define task configurations in YAML and attach the model in Python using `CrewBase`:<br><br>1. 1<br>2. 2<br>3. 3<br>4. 4<br>5. 5<br>6. 6<br><br>1. `@task`<br>2. `def blog_task(self) -> Task:`<br>3.     `return Task(`<br>4.         `config=self.tasks_config['blog_task'],  # From YAML`<br>5.         `output_json=BlogSummary                 # Defined in Python`<br>6.     `)`<br><br>Copied!Wrap Toggled!<br><br>This approach combines YAML's ease of editing with Python's strict schema enforcement.|
|**Run the crew**|Execute the crew as usual using `crew.kickoff()`. The returned result includes structured data:<br><br>- `result.raw`: Raw model output<br>- `result.json_dict`: Dict output (if using `output_json`)<br>- `result.pydantic`: Pydantic object (if using `output_pydantic`)<br><br>You can also use dictionary-like access with `result["title"]` due to implemented `**getitem**` support.|
|**Use the structured data**|With structured output, you can cleanly feed data into downstream systems, pass it to other tasks, or serialize it:<br><br>1. 1<br>2. 2<br><br>1. `title = result.pydantic.title  # if using output_pydantic`<br>2. `title = result.json_dict.get("title")  # if using output_json`<br><br>Copied!Wrap Toggled!<br><br>This makes AI output a reliable part of your program’s data pipeline—no parsing or guesswork required.|

---

## Why structured output matters in CrewAI

Now that we've seen how to define and apply Pydantic models in CrewAI, it's important to understand why this practice is so valuable in real-world workflows. The following table outlines the practical benefits of using structured outputs—not just in theory, but in how they help CrewAI applications become more robust, maintainable, and production-ready.

|Benefit|How it helps in CrewAI workflows|
|---|---|
|**Type safety and validation**|CrewAI validates the LLM output against the schema you define. If the model returns incorrect types or misses required fields, you're immediately notified. This prevents subtle bugs from creeping into your pipeline.|
|**Clear data contracts**|A Pydantic model acts like a formal agreement: "This task will always return these fields, with these types." This makes the codebase easier to understand, especially in collaborative projects where agents and tasks are reused.|
|**System integration**|Whether you're pushing the output to an API, saving it to a database, or displaying it in a UI, structured outputs make integration seamless. There's no need to manually parse or clean the LLM response.|
|**Less post-processing**|Without structured outputs, developers often write custom parsing or regex logic to extract information from raw text. With CrewAI and Pydantic, the heavy lifting is handled for you—validated, parsed, and ready to use.|
|**Consistent agent handoffs**|In multi-agent workflows, structure ensures smooth transitions. One agent's output becomes the next agent's input, without ambiguity. This avoids hallucinated formats or misinterpretation between agents.|
|**LLM behavior alignment**|When LLMs are prompted to follow a structured schema (e.g., "Return a JSON with fields A, B, and C"), they are more likely to stay focused and accurate. It works like soft prompting or function-calling—constraining the model's output space.|

## Summary

Structured outputs in CrewAI let you combine the flexibility of language models with the reliability of defined data formats. By using Pydantic models, you create a clear structure that CrewAI enforces, making outputs easier to validate, reuse, and integrate. This approach helps you build more reliable workflows, connect multiple agents smoothly, and plug AI results directly into real systems. It's a key step in turning experimental AI into production-ready applications.


Play

00:00

00:00

Mute

Settings

# Cheat Sheet: CrewAI Fundamentals and Advanced Applications

**Estimated time:** 15 minutes

### 1. What is CrewAI?

CrewAI is a framework for orchestrating autonomous AI agents, enabling them to collaborate on complex tasks. It allows you to build a "crew" of agents, each with a specific `role`, `goal`, and `tools`, who work together to achieve an objective, much like a human team. This approach is ideal for automating multi-step workflows, from research and analysis to content creation and customer service.

---

### 2. Core Components of a Crew

A CrewAI system is built from three main components: **Agents**, **Tasks**, and the **Crew** itself.

#### AI Agents

Agents are the individual workers in your crew. Each one is an autonomous AI with a defined purpose.

|Attribute|Description|
|---|---|
|**Role**|The agent's job title or function (e.g., "Nutrition Analyst").|
|**Goal**|The specific objective the agent is meant to achieve.|
|**Backstory**|Context or personality that shapes the agent's behavior.|
|**Tools**|A list of functions or capabilities the agent can use (e.g., web search, PDF reader).|
|**llm**|The language model that powers the agent's reasoning.|
|**verbose**|Is a boolean parameter; if `True`, it enables detailed logging of the agent's thought process.|

**Example: Creating an Agent**

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

16. `from crewai import Agent`
17. `from crewai_tools import SerperDevTool`

18. `# Initialize a search tool`
19. `search_tool = SerperDevTool()`

20. `# Define an agent and provide it with the search tool`
21. `research_agent = Agent(`
22.   `role='Senior Research Analyst',`
23.   `goal='Uncover cutting-edge information on a given topic',`
24.   `backstory='An expert researcher skilled at synthesizing data.',`
25.   `tools=[search_tool],`
26.   `llm=my_llm, # An initialized LLM`
27.   `verbose=True`
28. `)`

Copied!Wrap Toggled!

#### Tasks

Tasks are the specific assignments given to agents. They define what needs to be done and what the expected outcome is.

|Attribute|Description|
|---|---|
|**Description**|A clear explanation of the assignment, often with placeholders like {topic} for dynamic inputs.|
|**Expected Output**|A description of what a successful result should look like.|
|**Agent**|The agent assigned to complete the task.|
|**Context**|A list of other tasks whose output this task depends on.|
|**Tools**|A list of tools specifically provided for this task (see Section 3).|
|**output_pydantic**|A Pydantic model to structure the task's output (see Section 4).|

**Example: Creating a Task**

1. 1
2. 2
3. 3
4. 4
5. 5
6. 6
7. 7
8. 8

9. `from crewai import Task`

10. `# Define a task for the research_agent`
11. `research_task = Task(`
12.   `description='Analyze the major trends in {topic}.',`
13.   `expected_output='A detailed report on key trends and technologies.',`
14.   `agent=research_agent`
15. `)`

Copied!Wrap Toggled!

#### Crews

The Crew brings everything together, managing the agents and tasks according to a defined process.

|Attribute|Description|
|---|---|
|**Agents**|A list of all agents in the crew.|
|**Tasks**|A list of all tasks to be executed.|
|**Process**|The execution strategy. `Process.sequential` runs tasks one after another. `Process.hierarchical` allows for more complex, delegation-based workflows.|

**Example: Assembling and Running a Crew**

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

15. `from crewai import Crew, Process`

16. `# Create the crew with a sequential process`
17. `content_crew = Crew(`
18.     `agents=[research_agent, writer_agent],`
19.     `tasks=[research_task, writer_task],`
20.     `process=Process.sequential,`
21.     `verbose=True`
22. `)`

23. `# Start the crew's work with a specific input`
24. `result = content_crew.kickoff(inputs={'topic': 'AI in Healthcare'})`

25. `print(result)`

Copied!Wrap Toggled!

---

### 3. Structuring Workflows: Agent-Centric vs. Task-Centric Tools

A key design choice in CrewAI is _how_ you provide tools to your agents. This choice impacts the efficiency and reliability of your system.

#### The Generalist (Agent-Centric Approach)

This is the standard method where you give an agent a full "toolbox" of all the tools it might need. The agent uses its own reasoning to decide which tool to use for a given task.

- **Pro:** Simple to set up
- **Con:** Can be inefficient and unpredictable, as the agent may choose the wrong tool or take longer to decide

**Agent-Centric Code Snippet**

1. 1
2. 2
3. 3
4. 4
5. 5
6. 6

7. `# The agent is given a toolbox with multiple tools`
8. `generalist_agent = Agent(`
9.     `role='Inquiry Specialist',`
10.     `goal='Answer all customer questions.',`
11.     `tools=[pdf_search_tool, web_search_tool] # Agent must choose`
12. `)`

Copied!Wrap Toggled!

#### The Specialist (Task-Centric Approach)

In this more advanced and robust approach, you assign tools directly to the tasks that require them. When you assign tools to a task, CrewAI completely overrides the agent's tools for that specific task so only the tools it needs for that job are used.

- **Pro:** More efficient, predictable, and secure. It eliminates ambiguity and focuses the agent's efforts
- **Con:** Requires a more structured, multi-task workflow

**Task-Centric Code Snippet**

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

15. `# The agent is not given tools directly`
16. `specialist_agent = Agent(`
17.     `role='Customer Service Specialist',`
18.     `goal='Follow a step-by-step process to answer questions.',`
19.     `tools=[] # No tools assigned to the agent; however, if tools are provided they are overridden`
20. `)`

21. `# Each task gets its own specific tool`
22. `faq_search_task = Task(`
23.     `description="Search the FAQ PDF for the query: '{customer_query}'",`
24.     `expected_output="Relevant info from the PDF.",`
25.     `tools=[pdf_search_tool], # Tool is specific to THIS task`
26.     `agent=specialist_agent`
27. `)`

Copied!Wrap Toggled!

---

### 4. Structuring Output Data with Pydantic

To ensure your agents produce consistent, reliable, and structured data (like JSON), you can use Pydantic models. By defining a `BaseModel`, you create a template for the agent's output.

**Example: Defining and Using a Pydantic Model**

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

18. `from pydantic import BaseModel, Field`
19. `from typing import List #Used to ensure that the AI's output is a list of strings`

20. `# 1. Define the data structure`
21. `class GroceryShoppingPlan(BaseModel):`
22.     `"""Complete simplified shopping plan"""`
23.     `total_budget: str = Field(description="Total planned budget")`
24.     `meal_plans: List[str] = Field(description="Planned meals")`
25.     `shopping_tips: List[str] = Field(description="Money-saving tips")`

26. `# 2. Assign the model to a task's output`
27. `shopping_task = Task(`
28.     `description="Organize a shopping list for {meal_name}.",`
29.     `expected_output="An organized shopping plan.",`
30.     `agent=shopping_organizer,`
31.     `output_pydantic=GroceryShoppingPlan`
32. `)`

Copied!Wrap Toggled!

---

### 5. Advanced Crew Management with @CrewBase and YAML

For larger, production-level projects, CrewAI offers a powerful way to organize your agents and tasks using the `@CrewBase` decorator and YAML configuration files.

- **`@CrewBase` Decorator:** A Python class decorator that automates the setup of your crew by discovering methods marked with `@agent` and `@task`.
- **`@crew` Decorator:** An optional decorator used inside a `@CrewBase` class that marks the specific method responsible for assembling the agents and tasks into a final `Crew` object. This method defines which agents and tasks are part of the crew and sets the execution process (e.g., `Process.sequential`).
- **YAML Configuration:** Allows you to define your agents' and tasks' properties (like `role`, `goal`, `description`) in separate `agents.yaml` and `tasks.yaml` files. This separates configuration from code, making your project cleaner and easier to manage.

> **Crucial Note:** The `@CrewBase` class relies on Python's `inspect` module to find file paths, which **does not work correctly inside a Jupyter Notebook**. For this reason, you should always define your `@CrewBase` classes in separate **`.py` files** and import them into your main application.

**Example: Conceptual Structure in a `.py` file**

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
27. 27

28. `# In a file named 'my_crew_defs.py'`
29. `from crewai.project import CrewBase, agent, task, crew`
30. `from crewai import Agent, Task, Crew, Process`

31. `@CrewBase`
32. `class FinancialCrew:`
33.     `"""A class to manage the financial analysis crew."""`
34.     `agents_config = 'config/agents.yaml'`
35.     `tasks_config = 'config/tasks.yaml'`

36.     `@agent`
37.     `def market_analyst(self) -> Agent:`
38.         `return Agent(config=self.agents_config['market_analyst'])`

39.     `@task`
40.     `def analysis_task(self) -> Task:`
41.         `return Task(config=self.tasks_config['analysis_task'])`

42.     `@crew`
43.     `def crew(self) -> Crew:`
44.         `"""Assembles the agents and tasks into a crew."""`
45.         `return Crew(`
46.             `agents=[self.market_analyst()],`
47.             `tasks=[self.analysis_task()],`
48.             `process=Process.sequential,`
49.             `verbose=True`
50.         `)`