# Agentic-workflow-Langgraph

Multi-agent systems

1] Agent is system that LLM uses to decide the control flow of an application.
2] Agent has too many tools as its disposal and makes poor decision about which tool to call next.

# Multi Agent Architecture:
1] Network- Each Agent communicate with every other agent,
2] Supervisor- Each agent communicates with single supervisor agent. Supervisor agent make decision on which agent should call next.
3] Supervisor(Tool calling)- Individual agents can be represented as tools, Supervisor uses tool calling LLM to decide which agent
   agent tools to call as well as arguments to pass to those arguments.
4] Hierarchical - Supervisor of supervisor, allows for more complex control and flows
5] Cutsom multi-agent Workflow - Each agent sommunicates with only subset of agents. Parts of flow are deterministic, only
   some agents can decide which other agents to call.

  # Handoffs
  
