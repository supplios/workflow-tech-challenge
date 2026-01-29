# Supplios – Full Stack Engineer Interview Challenge  (2026)

## **Workflow Engine for Business Processes**

## **Introduction**

One of the most common problems in software development is managing the state of a long-running process. This can be as simple as a user signing up for a service, or as complex as a multi-step process in a business workflow.  How to define the process, track where things are at in the running process, data about the process, permissions for who an see/edit/do what, etc.  

We want to see how you would approach this problem and how you would design a solution to it, as it is a common problem in our domain and one of the core features of our platform.

We are more focused on looking at your general approach and architecture rather than the small implementation details.  

NOTE: We assume people will use AI at least to help with this. If you do, please disclose that, describe how you used it, what direction you gave it, etc.  Then when we review it with you, we'll ask why certain decisions were made, which you should be responsible for yourself (instead of just saying "because Claude/Gemini/Codex did it that way").  

## **Practical Details**

- **Time Expectation**: Spend **1–2 hours**. We value your **approach**, not a full-fledged solution.
- **Programming Language**: Use any language you're comfortable with (but Python is slightly preferred). The focus is on your **problem-solving skills**.
- **Code Expectations**: Deliver **clean, well-structured code** that is readable and maintainable.  Add comments to explain things or mention things you did not have time to implement.
- **Provide Documentation**:
  - A **brief explanation** of your solution.
  - Instructions on **how to run your code**.
  - Any other relevant notes or insights.
  - If you used AI, describe how you used it, direction you gave it.

## **The Challenge**

You will implement a **state management and workflow system** with the following components and behaviors:

### **Core Components**

1. **Workflow**: Represents the overall process engine and has it's own **state**.
2. **Tasks**: Sub-components of a workflow, each with it's own **state**.
3. **Links**: Define the relationships between a source component and a target component, and how source component state changes affect the target component to linked state changes.

#### **Link Abstraction**

To manage these relationships, implement a dedicated link abstraction that explicitly defines the relationships and their effects. This abstraction should include:

- **Source Component**: The component (Workflow or Task) that initiates the state change.
- **Target Component(s)**: The component (Workflow or Task) affected by the state change.
- **State Transition Rules**: The specific rules that define how a state change in the source component affects the target component. For example, "if Task A moves to `In Progress`, Task B should move to `In Progress`."

#### **Link Interactions**

The system should handle the following scenarios:

1. Changing a **Workflow** state affects only its linked **Tasks** states.
2. Changing a **Task** state affects other linked **Tasks** or the linked **Workflow** state.
3. Any state transitions for **Workflow** and **Tasks** are valid, but the links should define the valid transitions.
   - From any state to any other state.
   - Even going back to a previous state.

### **Challenge Goal**

Build a program that can:

1. **Create** a Workflow execution.  (a "running" stateful instance of a defined workflow process)
2. **Create** Task executions.  ("running" stateful instances of tasks)
3. **Use** Links to control the execution flow of the Workflow.
4. Put the pieces together to form a **Workflow Engine** that can manage the state transitions of the Workflow and Tasks based on the Links.
5. **Update** the state of a Workflow or Task and ensure that the state changes cascade correctly according to the Links.

Model out one flow and demonstrate how the system can manage the state transitions.

Example of a business process to model with your Workflow (But feel free to use some other business process in your example!):

```
Workflow: Onboarding
Tasks: [
   Sign Up,
   Verify Email,
   Add Profile
]
States: [
   Pending,
   In Progress,
   Completed
]

Example:
   - A state change in the Workflow or any of it's Tasks can trigger state changes in other Tasks or the Workflow.
      - So either 'Onboarding' or 'Sign Up' moving to 'In Progress' could trigger the other to move to 'In Progress'.
   - State changes can be linear, parallel, or conditional.
      - So 'Sign Up' moving to 'Completed' could trigger 'Verify Email' and 'Add Profile' to move to 'In Progress'.
   - Conditional side effects occur only when specific requirements are met.
      - A conditional could be a merge point where multiple Tasks must reach a specific state before the Workflow can move to the next state.
      - So when 'Verify Email' and 'Add Profile' are both 'Completed', 'Onboarding' moves to 'Completed'.
```

## **Deliverables**

1. **Code**:
   - Ensure it is modular and easy to extend.
   - Focus on clean architecture and readability.
2. **Documentation**:
   - Explain how your system works.
   - Any assumptions you made.
   - Describe how to run your code.
   - How you used AI, if you did.
3. **Bonus** (Optional):
   - Add tests.
   - Provide a diagram or flowchart illustrating your system's workflow.

### How to submit:

Submit your solution either of these ways:
- Send us a link to a public repo, or invite us to a private repo (GitHub handle is @hamblin)  OR...
- Send us a .zip of a a project with clear instructions for how to run it, and related comments

Thanks!
