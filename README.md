# Agentic-workflow-Langgraph

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

# Handoffs
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
   # Payload: 
      1. Agents communicate via handoffs and pass the graph state as part of handoff payload.
      2. Agents pass around list of messages as part of graph state
      3. In case of supervisor with tool calling, the payloads are tool call arguments.
      

