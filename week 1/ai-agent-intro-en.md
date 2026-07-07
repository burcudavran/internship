# Week 1: Fundamental Concepts and Introduction to Microsoft Agent Framework

## What is an AI Agent?

AI agents are autonomous software systems that use artificial intelligence to perform complex tasks and achieve specific goals without requiring human intervention. They possess a wide range of capabilities including decision-making, problem-solving, interacting with external environments, and executing goal-oriented actions.

At their core, they are powered by Large Language Models (LLMs). This enables them to process multimodal data such as text, audio, video, and code. However, traditional LLMs are static; they are limited to the data they were trained on. They cannot access live data or take autonomous action.

AI agents, on the other hand, have a dynamic structure. They combine the reasoning ability of LLMs with tool/function calling, memory, and dynamic workflows, allowing them to go beyond their training data. This enables them to perform autonomous and complex tasks.

**Tool Calling:** The ability of an AI to autonomously consult external systems or resources to expand its capabilities, interact with its environment, and complete tasks.

## Key Features That Make AI Agents Powerful

### Reasoning

The agent's ability to process input data and context through a logical filter to derive meaning.

Using Chain-of-Thought or ReAct (Reason + Act) templates, the AI is enabled to run an internal logical reasoning loop before taking action.

**ReAct (reason + act):** A framework that combines the thinking and acting capabilities of AI. With the ReAct paradigm, agents are instructed to think after each tool response and action they take, and to plan which tool to use in the next step.

It operates in cycles called: Think - Act - Observe. This allows agents to solve problems step by step, progressively improving their responses.

**Chain-of-Thought:** An approach where agents reason slowly through a given prompt and explicitly articulate each thought.

This allows for transparent insight into how the agent approaches a question and formulates its answers.

**In summary:** ReAct provides the action cycle where the agent interacts with the outside world (tools) and observes results, while Chain-of-Thought is the mechanism that enables the agent to "think out loud" and reason step by step in the background. Together, they allow agents to research and solve problems just like a human would.

### Planning

The agent creates a strategic plan to achieve a given complex goal, identifies necessary steps, and breaks actions down into smaller subtasks.

When faced with a complex problem, the agent does not try to solve it in a single step. It plans step by step and can modify its plan when encountering an obstacle.

### Tool/Function Calling

The agent stepping out of the static LLM world to interact with and leverage external resources.

### Memory

The agent's ability to store past interactions, user preferences, and intermediate results obtained during tasks, and recall them when needed.

- **Short-Term Memory:** The agent's ability to keep track of the immediate flow of the current conversation or task. This refers to the context window of AI models. The chat history with the user is fed back to the model with each new request. This ensures that what happened in the previous sentence is not forgotten.

- **Long-Term Memory:** The agent's ability to recall information learned in the past, user preferences, and historical data even after tasks or sessions have ended. Data is stored in vector or relational databases. When the agent receives a new task, it retrieves past information from the database using semantic search.

- **Episodic Memory:** The agent's ability to store specific past actions, scenarios, and lessons learned (successes or failures) from those scenarios as memories.

- **Shared Memory:** A common knowledge pool shared among different agents in multi-agent architectures.

### Autonomy

The agent's freedom to make decisions and take actions in line with given tasks without requiring human intervention or approval mechanisms at every step.

## Types of AI Agents

AI agents are categorized by their capabilities, working structures, and forms of interaction with the user.

### By Capacity and Complexity Level

- **Simple Reflex Agents:** The simplest type of agent. They have no memory. They respond to the question "What do I see right now?" They do not interact with other agents and act based on predetermined rules driven only by current perceptions. They do not react to unexpected situations.

- **Model-Based Reflex Agents:** Using their current perceptions and memory, they can track the state of the outside world, building and updating an internal model of it. They have state management mechanisms and memory.

- **Utility-Based Agents:** They focus not just on reaching the goal but on how to reach it with the highest efficiency and utility. They operate a utility function. They make decisions based on fixed criteria defined in workflows.

- **Goal-Based Agents:** They have a defined goal. They explore sequences of actions and make plans to achieve the goal. This is where planning ability originates. The agent calculates alternative paths to the goal using search and planning algorithms.

- **Learning Agents:** They expand their knowledge by learning from new experiences on their own and improve their performance as they gain experience.

### By Interaction Type

Agents are divided into 2 types based on their ability to communicate with the user:

- **Surface Agents / Interactive Partners:** Agents that communicate directly with the user, typically triggered by user input.

- **Autonomous Background Processes:** Agents that run in the background without direct input, triggered by events or tasks.

### By Working and Architectural Structure

- **Single Agents:** Independent agents that use external resources and tools on their own to achieve a specific goal. Suitable for tasks that do not require collaboration and have clearly defined boundaries.

- **Multi-Agent Systems:** Suitable for multi-step, large tasks and projects. Systems consisting of multiple agents that communicate with each other and combine their expertise for a common goal or competition.

## Differences Between Chatbots and AI Agents

The key differences between AI agents and standard chatbots lie in their level of autonomy, capacity to manage complex tasks, learning abilities, and how they approach goals.

### Autonomy and Interaction Type

- **Chatbot:** Low autonomy. They work reactively. They require pre-programmed commands, triggers, or user input to take action.
- **AI Agent:** Autonomous and proactive. They can make independent decisions and take action to complete tasks toward a final goal without needing step-by-step human planning or intervention.

### Reasoning and Task Planning

- **Chatbot:** They operate with rule-based or scripted logic. They respond by stringing together the most statistically appropriate words for the given input. They have no long-term plan.
- **AI Agent:** They have advanced reasoning and strategic planning capabilities. They use thought templates (e.g., ReAct). They break complex tasks into sub-tasks and can flexibly adapt by interacting with their external environment based on changing conditions.

### Memory, Learning, and Personalization

- **Chatbot:** They generally have no memory and limited learning abilities. This deficiency prevents them from personalizing the user experience and learning from their mistakes.
- **AI Agent:** They possess 4 types of memory that can store past interactions. This allows them to self-improve their performance, learn from user behavior, and offer increasingly higher levels of personalized experiences over time.

### Tool/Function Calling

- **Chatbot:** They cannot access external tools or systems to compensate for their lack of knowledge.
- **AI Agent:** They can autonomously access external tools or systems to interact with the outside world and keep themselves updated.
