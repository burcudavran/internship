# Week 1: Fundamental Concepts and Introduction to Microsoft Agent Framework

## What is an AI Agent?

AI agents are autonomous software systems that use artificial intelligence to perform complex tasks and achieve specific goals without requiring human intervention. They possess a wide range of capabilities including decision-making, problem-solving, interacting with external environments, and executing goal-oriented actions.

At their core, they are powered by Large Language Models (LLMs) and, when needed, supported by multimodal models to process multimodal data including text, audio, video, and code. However, traditional LLMs are static; they are limited to the data they were trained on. They cannot access live data or take autonomous action.

AI agents, on the other hand, have a dynamic structure. They combine the reasoning ability of LLMs with tool/function calling, memory, and dynamic workflows, allowing them to go beyond their training data. This enables them to perform autonomous and complex tasks.

**Tool Calling:** The ability of an AI to autonomously consult external systems or resources to expand its capabilities, interact with its environment, and complete tasks.

## What is an LLM (Large Language Model)?

In its most basic definition, a Large Language Model (LLM) is a deep learning-based AI system trained on massive amounts of text data, capable of understanding and generating human-like language.

At their core, LLMs are massive statistical prediction machines. When a prompt is given to the model, it does not pre-plan the response. Using the language rules it has learned from its training data, it predicts the most appropriate next word (token) based on the context.

The word "large" in the name refers both to being trained on datasets containing billions of words and to having mathematical weights — reaching billions or even trillions of parameters — that the model uses internally to make decisions. The larger the model, the higher its capacity to imitate human language and produce accurate responses.

### How LLMs Work

The underlying process of Large Language Models consists of multi-layered and complex stages, from raw data input to generating fluent text for the user.

#### Tokenization

Models cannot read words directly. Input texts (prompts) are broken down into small, meaningful pieces (words or syllables) called tokens, which the machine can process.

#### Embedding

Language models cannot read words; they can only perceive numbers. Therefore, the obtained tokens are converted into multi-dimensional numerical vectors called embeddings. Semantically similar words are positioned close to each other in this mathematical space.

#### Transformer and Self-Attention

At this stage, the transformer architecture and self-attention mechanism come into play.

Introduced in the 2017 paper "Attention Is All You Need" by Google researchers, the Transformer architecture is a neural network structure that forms the foundation of today's Large Language Models. It enables LLMs to understand and generate human language.

Older-generation AI systems had to process words sequentially, one by one — just like humans reading a book. This slowed down the system and made it difficult for the model to retain relationships between words at the beginning and end of a sentence.

The Transformer architecture solved this problem with two key innovations:

1. **Parallel Processing:** Instead of reading words sequentially, Transformers process the entire text or word sequence simultaneously, in parallel. This enabled models to be trained on massive amounts of data in much less time by fully utilizing the power of modern hardware.

2. **Self-Attention:** The biggest innovation of the Transformer architecture. Self-attention allows the model to simultaneously calculate which words are related to each other, regardless of the distance between them in a long sentence.

##### How It Works

When a question is given to the model, the Transformer breaks the text into tokens, then converts them into vectors. Through the self-attention mechanism, it extracts the contextual map of the entire sentence and the relationships between words. In the final step, it calculates and generates the most logical next word to add to the sequence based on this learned context.

The system uses learned statistical probabilities to predict the next most logical word to add to the sequence. The generated word is fed back into the system, and the process continues — predicting the next word — until the response is complete.

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

- **Interactive Agents:** Agents that communicate directly with the user, typically triggered by user input.

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

## Why an Agent Is Not Just a Prompt-Writing System

The fundamental reason AI agents are not merely prompt-writing systems is that a prompt is a one-time, passive instruction, whereas an agent is an autonomous architecture capable of achieving its own goals, making decisions, using external tools, and interacting with its environment.

The key differences that distinguish an AI agent from a simple prompt-based system:

One of the most important differences is that prompt creation and processing is only a sub-component of the agent architecture, not the entirety of it. A goal-driven agent generates its own prompts instead of waiting for external prompts.

A prompt is a command that only tells the model what to do at a specific moment and depends on human intervention. Agents, on the other hand, are fully autonomous; they make and execute the decisions needed to achieve their goals.

Prompt-based interactions are typically stateless by nature — the system has no obligation to remember history. Each command is processed as if seen for the first time. AI agents, however, have multi-structured memory systems, including 4 types of memory. This allows them to maintain context throughout a task, learn from past actions, and act according to the current state.

A prompt is merely a text string confined within the language model, unable to be affected by the outside world. Agents are autonomous structures connected to external applications and systems.

A prompt is singular and instantaneous. A single response is produced for the given command, and the process ends. Agents, through paradigms like ReAct, continuously operate in a perception, decision, and action loop.

In summary, a prompt is a static, text-based command that tells a model what to do, while an AI agent is complex software that organizes these commands on its own, updates its state, and exchanges data with the outside world.

## Core Components of Agent Architecture

**Agent:** An autonomous system that can perceive its environment, make decisions, and take action in the external world to achieve a specific goal. Each agent has its own role, internal state, and objective.

**Tool:** External resources or functions that agents use to interact with the outside world and expand their capabilities. They can use tools such as databases, web searches, APIs, graphical or programmatic interfaces, or other agents to access up-to-date information or perform digital actions. The autonomous invocation and use of these tools (tool calling) enables agents to solve real-world problems.

**Memory:** The core component that allows agents to maintain context throughout a task, learn from past experiences, and improve over time by adapting. This mechanism prevents agents from repeating mistakes, adapts to user preferences, and enables more accurate, personalized behavior.

**Workflow:** The autonomous sequence of task steps that an agent designs and orders to solve a complex problem and achieve its goal. The process begins with creating a plan, breaking the task into subtasks, and taking action. Workflows can be managed by reasoning paradigms and may also encompass multi-agent systems.

**MCP:** An open-source, standardized communication protocol that enables AI applications to connect to external systems, data sources, and tools.

## MCP (Model Context Protocol)

It works like a universal USB-C that connects electronic devices. It enables AI models to interact with external systems in a standardized way.

The biggest limitation of Large Language Models (LLMs) is that they are static — confined to the data they were trained on and unable to autonomously communicate with the outside world. MCP acts as a bridge that removes these limitations.

MCP is one of the key standards that allows AI to break free from dependence on static training data, pull real-time data from external sources, fill knowledge gaps, and keep itself updated. However, MCP is not a closed box limited to LLMs; it is a fully open-source and universal protocol.

### Core Architecture and How It Works

It consists of 3 main components:

**MCP Host:** The layer where the model and user interact. It hosts the LLM and the interface the user interacts with. It runs one or more MCP Clients in the background.

**MCP Client:** Runs inside the Host. It translates the model's requests into a format MCP understands, and MCP's requests into a format the model understands. It also discovers available MCP servers. It typically runs as a library or SDK embedded within the agent framework being used.

**MCP Server:** An external service that provides context, data, or external tool capabilities to the LLM. These are small, isolated services that translate external data sources or tools into the common language understood by the protocol.

### What It Provides and Why It Matters

- Prevents LLMs from hallucinating (which occurs when relying solely on training data) by enabling connections to reliable, real-time external data sources.
- Transforms AI from a mere text-generating chatbot into a system capable of true autonomy.
- Eliminates fragmented integration efforts by providing a single, standard protocol. This reduces development time, costs, and complexity.
- Being standard and open-source, it enables model switching without requiring major changes to the host system.

## Microsoft Agent Framework

Microsoft Agent Framework is an open-source framework designed for building, orchestrating, and deploying autonomous AI agents and multi-agent workflows into production environments.

AI agents are developed to overcome the static nature of LLMs and manage complex processes autonomously. Microsoft Agent Framework is the set of tools and services used to develop and manage these agents.

The main goal is to build autonomous systems that perform complex tasks — going beyond one-time commands to interact with external systems, maintain memory, and solve complex problems autonomously.

It is the direct next generation of Semantic Kernel and AutoGen, combining AutoGen's simplicity in creating single and multi-agent systems with Semantic Kernel's enterprise-grade capabilities under a single roof.

### Core Architectural Components

The framework's architecture is built on two main components to handle tasks of varying complexity:

**Agents:** Autonomous units that use large language models as their "brain" to process inputs, use external tools, and generate autonomous responses. They are used in open-ended, conversation-based scenarios where the agent needs to select its own tools and make autonomous decisions. Supports various model providers including Microsoft Foundry, Azure OpenAI, Anthropic, and Ollama.

**Workflows:** Connect multiple agents, human interactions, and external systems in a graph-based structure for multi-step tasks. Used when tasks have clear steps and precise control over execution order is required.

#### Workflow API Types

Workflows offer 2 different APIs:

**Functional API:** The most natural and simple method, designed using standard code loops. Uses decorators such as `@workflow` and `@step` for control flow. Preferred when operations are mostly sequential, have specific loops, or need to be solved with straightforward logic.

**Graph API:** An advanced method where the process is drawn with strict boundaries as a directed graph. Agents or custom logic are defined as "executors," and message paths between them are defined as "edges." Which agent receives which message is enforced through strict type validation. This API is preferred when the process architecture is fixed, tasks are highly detailed, and strict message routing rules are needed.

### MCP Support

MAF supports MCP (Model Context Protocol), enabling agents to connect to external data sources, applications, and tools in a standard and secure way.

### Enterprise-Ready Production Features

To take agents from prototype to production with confidence, MAF inherits the following enterprise capabilities from Semantic Kernel:

**Checkpointing:** Prevents long-running processes from being lost entirely. The system saves its current state, allowing the process to be recovered and resumed from where it left off.

**Observability:** Removes the "black box" nature of agent actions by providing distributed tracing and debugging capabilities.

**Middleware:** Allows custom pipelines to be created between agent requests and responses, making error handling and security management easier.

**Human-in-the-Loop (HITL):** Built-in mechanisms that automatically pause workflows before critical decisions and wait for human approval or input.
