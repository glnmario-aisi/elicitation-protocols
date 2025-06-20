# Elicitation During Testing Exercises
This document is a preliminary draft and not exhaustive. If you have any questions about which elicitation setting is best for your setup or need confirmation, please post in the [#ru-elicitation](https://aisecurityinstitute.slack.com/archives/C06HFEN9RH6) channel on Slack. For additional information and a more comprehensive overview, please refer to the [Elicitation Best Practices](https://github.com/glnmario-aisi/elicitation-protocols/blob/main/checklist.md) document.

## Checklist 
When working with a new model or task, we should start by understanding and addressing any failure modes. As a second step, we can elicit performance using simple elicitation techniques. Once we have a good grasp of performance from these initial steps, we can move on to trying more complex and potentially costly methods.

#### Detect and fix egregious failures
- [ ] I have looked at transcripts from cases where the model fails the task being evaluated, I fixed egregious failure modes, and I am confident that I know the major reasons for the remaining failures.
     - [ ] I have verified that the model is not failing due to refusals. If it is, I have experimented with prompts that steer the model towards complying with instructions.
     - [ ] I have verified that prompt and chat messages are properly formatted (e.g., keeping indentation and paragraph structure intact).
     - [ ] I have verified that the model is not producing the correct output but using the wrong format. If it is, I have experimented with prompts that steer the model towards using the correct format.
     - [ ] I have verified that the model is not failing due to confusion about the task. If it is, I have experimented with clarifying the prompt.
     - [ ] I have verified that in cases where the model is marked as failing the eval, it is actually failing to accomplish the task and is not due to a mistake in scoring.
  <details><summary>What if there are mistakes in scoring?</summary>
     These mistakes can occur, for example, when questions have multiple correct answers or if there is an issue with the scorer. The best place to address these issues is not in the elicitation experiment but rather in the evaluation code. Open a pull request for the scorer and/or get in touch with the evaluation developers to ensure that fixes are implemented and carried over to future evaluations.
</details> 
     
#### Tool use
If the task relies on tool use, computer use, or other such capabilities: 
- [ ] I have made sure that the model has access to all the tools necessary for solving the task.
- [ ] I have verified that the model uses the correct format (e.g., that it doesn't incorrectly escape newlines) when calling tools. This is a failure mode to look out for both in failed tool calls and "successful" tool calls where the arguments are incorrect.
- [ ] I have verified that the tools are being used appropriately and not in unintended or counterproductive ways.
     - [ ] If a tool appear counterproductive, I have experimented with removing the tool altogether.
- [ ] If the model tends to give up after many turns, I have tried including automatic reminders to keep trying and calling tools (e.g., if the model hasn't called a tool in its last *n* turns).
     
#### Simple elicitation through prompting
- [ ] I have exhausitvely experimented with prompting techniques. 
     - [ ] I have asked in [#ru-elicitation](https://aisecurityinstitute.slack.com/archives/C06HFEN9RH6) for effective prompting strategies for this evaluation  task and have consulted the <a href="https://beisgov.sharepoint.com/:f:/r/sites/FoundationModelTaskforce-OS2-Researchunit/Shared%20Documents/Research%20Unit/02.%20Workstreams/8.%20Platform/7.%20Capability%20Elicitation/Projects%20-%20Summaries?csf=1&web=1&e=QK2YUY">Projects - Summaries</a> SharePoint.
     - [ ] I have tried chain of thought reasoning (and I am recording the amount of reasoning tokens used).
     - [ ] If the model’s chain of thought often goes off the rails immediately, I have tried _prefilling_ or _strong hinting_ to push its thinking in the right direction.
          <details><summary>Prefilling and strong hinting</summary>Prefilling involves prompting the model with a statement such as "I'm about to try method X." Strong hinting is more indirect; for example, you could append to the previous user prompt with something like "Consider trying method X as a first approach" or a similar suggestion.</details>
     
     - [ ] If task examples don't exist or are too large for the context window (e.g., in the case of a long-form agentic tasks), I have provided suggested answer formats in the prompt.  
     - [ ] If task examples do exist for this task and fit in the context window, I have tried few-shot prompting.
     - [ ] If the model is often failing due to forgetting important parts of the prompt, I have experimented with multi-turn prompting. 
      
