## Agentic-workflow-Langgraph

# Multi-agent systems

1] Agent is system that LLM uses to decide the control flow of an application.
2] Agent can be represented as Graph Nodes
3] Agent has too many tools as its disposal and makes poor decision about which tool to call next.

# Multi Agent Architecture:
1] Network- Each Agent communicate with every other agent,
2] Supervisor- Each agent communicates with single supervisor agent. Supervisor agent make decision on which agent should call next.
3] Supervisor(Tool calling)- Individual agents can be represented as tools, Supervisor uses tool calling LLM to decide which agent
   agent tools to call as well as arguments to pass to those arguments.
4] Hierarchical- Supervisor of supervisor, allows for more complex control and flows
5] Cutsom multi- agent Workflow - Each agent sommunicates with only subset of agents. Parts of flow are deterministic, only
   some agents can decide which other agents to call.

## Handoffs
  In Multi Agent architcture, each agent node executes its task and decide whether to finish execution or route to another agent,
  including routing to itself was well.
  Handoffs is a concept where one agent handoffs control to another agent.
  Handoffs allows us to specify
     1] Destination; Target to navigate (Node).
     2] Payload; Information to pass to the agent (State update).

# Network Architecture
   1. Agents are defined as graph nodes
   2. Each agent can communicate with every other agent and can decide which agent to call next.

# Supervisor
   1. In this architecture, we define agents as nodes and add a supervisor node(LLM) that decides which agent node should be called next.
   2. We use "Command" to route execution to appropriate agent node based on supervisor's decision.
   3. This Architecture also supports running multiple agents in parallel or using map-reduce pattern.

   Supervisor Tool Calling:
   1. Supervisor agent is responsible for calling sub-agents, the sub-agents are exposed to supervisor as tools, and supervisor agent decides
      which tool to call next
   2. The Supervisor agent follows a standard implementation as an LLM running in while loop until it decides to stop.

# Hierarchical 
   As we add more agents to our system, it might become hard for supervisor to manage all of them. The Supervisor can start making poor decision
   about which agent to call next or the context might become too complex for single supervisor to keep track of.
   Creating specialized teams of agents managed by individual supervisors, and a top-level supervisor to manage the teams.

# Custom multi-agent workflow
   In these architecture, we add individual agents as graph nodes and define the order in which agents are called ahead of time in custom workflow
# Explicit Control Flow:
   Defining control flow of application explicitly via normal graph edges.
# Dynamic Control Flow:
   A special case of this is supervisor tool-calling architecture.

# Communication and state management

# How Agents Communicate?
   Common and generic way for agents to communicate is via a list of messages

# Handoffs vs Tool Calls
   ## Payload: 
      1. Agents communicate via handoffs and pass the graph state as part of handoff payload.
      2. Agents pass around list of messages as part of graph state
      3. In case of supervisor with tool calling, the payloads are tool call arguments.
![Screenshot 2025-07-07 014054](https://github.com/user-attachments/assets/af3d8aa7-4120-49cd-8160-f222c135ed26)

# Message passing between Agents
      1. Most common way for agents to communicate is via shared state channel(list of messages).
      2. This assumes that there is always atleast single channel in the state that is shared by agents.
      3. One more question arieses, while communicating: Should agents share the full history of their thought process pr only final result.
![image](https://github.com/user-attachments/assets/9718daba-9e01-4e2c-864f-ca90c2d8c493)

## Sharing full though process
   1. Agents can share the full history of their thought process (i.e Scratchpad) with all other agnets.
   2. Scratchpad means list of messages.
   3. Sharing full message history would help other agents to make better decisions and improve reasoning abilty of whole system.
## Sharing only final result
   1. Agents can have their own scratchpad and only share the final result with rest of agents
   2. This works well for complex system, we need to define agents with different state schemas

# Graph API
Langgraph models agents workflows as a graph and consist of 3 main components.
   1. State: Shared data structure that shares current snapshot of application, it is python type but is typically a 
             TypeDict or BaseModel.
   2. Nodes: Python function that encode the logic of agents. They recieve current state as a input and return updated state as output.
   3. Edges: Python functions that determine which Node to execute next based on the current State
## StateGraph
   This class is main graph class that is parameterized by state object.
   # StateMessages
   # Reducers

# Functional API
This allows us to add features such as persistence, memory, human-in-loop and streaming.
Uses two main building blocks
   1. @entrypoint- Marks a function as startinh point of a workflow
   2. @task- Represents a discrete unit of work i.e API call or data processing that can be executed asynchronously with entrypoint.

      

