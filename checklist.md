# Elicitation Checklist 
This checklist is designed to help you adopt **best practices for conducting elicitation experiments**. By following this checklist step-by-step, you can ensure rigor in your current experiments but also contribute to the broader goal of continuously improving AISI's testing methodologies. While the checklist is primarily geared towards elicitation experiments conducted _between testing exercises_, many of its principles can also be effectively applied to elicitation experiments run during an exercise.

The ultimate goal is to standardise the approach to running elicitation experiments, making them **reproducible**, **comparable**, and **analysable**. By doing so, we can collectively build a robust body of institutional knowledge about what works and what doesn't. This shared understanding of both positive and negative outcomes will, in turn, inform elicitation during testing exercises. 

<!--
🔴 High Priority 🟠 Medium Priority 🟢 Low Priority
-->

## Experimental setup 

- [ ] I have set a compute budget for this elicitation experiment.
     <details>
    <summary>What is a reasonable amount?</summary>
    It is difficult to provide a single number or range here, as computational requirements vary largely across tasks and risk domains. Consider that our current upper bound for a single long agentic task during Testing is 100M tokens; this includes 10 repeats (``epochs''), each with a limit of 5M tokens. Note that this is the most expensive type of task we currently run! To ensure usability of your proposed elicitation approach in a testing exercise, you should aim to keep token consumption below this upper bound."
    </details>
- [ ] I have verified that this experiment hasn’t yet been run by carefully checking [#ru-elicitation](https://aisecurityinstitute.slack.com/archives/C06HFEN9RH6)
    <details>
    <summary>What is #ru-elicitation?</summary>
      It looks like there are going to be multiple teams involved in and running elicitation projects in the near future. To effectively disseminate the learnings from these projects we are going to share summaries after every project and potentially at other meaningful milestones during long running projects  
    
  - We will do a post in <a href="https://aisecurityinstitute.slack.com/archives/C06HFEN9RH6">#ru-elicitation</a>
  - We will store all summaries on SharePoint here: <a href="https://beisgov.sharepoint.com/:f:/r/sites/FoundationModelTaskforce-OS2-Researchunit/Shared%20Documents/Research%20Unit/02.%20Workstreams/8.%20Platform/7.%20Capability%20Elicitation/Projects%20-%20Summaries?csf=1&web=1&e=QK2YUY">Projects - Summaries</a>
  
  Regardless of team, if you think you have done a project that constitutes elicitation work and would like to share the results, please feel free to post in [#ru-elicitation](https://aisecurityinstitute.slack.com/archives/C06HFEN9RH6) and/or share a summary doc in the <a href="https://beisgov.sharepoint.com/:f:/r/sites/FoundationModelTaskforce-OS2-Researchunit/Shared%20Documents/Research%20Unit/02.%20Workstreams/8.%20Platform/7.%20Capability%20Elicitation/Projects%20-%20Summaries?csf=1&web=1&e=QK2YUY">linked folder</a>.
  
  **Please share negative results as well as positive results.** Elicitation work is full of [tarpit ideas](https://www.ycombinator.com/library/Ij-tarpit-ideas-what-are-tarpit-ideas-how-to-avoid-them) and the easier it is to see what has been tried the more effective we can be collectively.
  </details>
  
- [ ] I have identified at least one appropriate baseline.
      <details>
      <summary>Why do we want a baseline? What is a reasonable baseline to use?</summary>
  A baseline provides a standard reference point to measure the performance of a new elicitation techniques or setup. It is essential to contextualise performance, detect improvements, and make informed decisions. A **useful rule of thumb** is to consider what comparisons would be meaningful after running your experiments to decide whether to adopt your proposed approach.
      
  - If I am testing a new technique (e.g., a new tool) or conducting a grid search over parameters (e.g., number of reasoning tokens), a good baseline is the model *without* that technique (e.g., without the tool, or with reasoning off).
  - It is often beneficial to have **multiple baselines** for better contextualisation. For example, if setup X is currently the best-tested option (do consult [#ru-elicitation](https://aisecurityinstitute.slack.com/archives/C06HFEN9RH6) and the <a href="https://beisgov.sharepoint.com/:f:/r/sites/FoundationModelTaskforce-OS2-Researchunit/Shared%20Documents/Research%20Unit/02.%20Workstreams/8.%20Platform/7.%20Capability%20Elicitation/Projects%20-%20Summaries?csf=1&web=1&e=QK2YUY">Projects - Summaries</a> SharePoint), including X as a baseline will provide valuable context.
  - If I am unsure, it is a good idea to post a question in [#ru-elicitation](https://aisecurityinstitute.slack.com/archives/C06HFEN9RH6).
  </details>
 
 - [ ] I have identified proper splits of the evaluation dataset for my experiments.
     - **Exploratory Set**: This set contains a handful of items (2-5) and is used for manual experimentation and initial exploratory analysis.
     - **Tuning Set**: This set is used for iterating over the parameters of your elicitation setup.
     - **Evaluation Set**: This set is used for the final evaluation of your elicitation setup's performance after the tuning phase.
     <details>
     <summary>How to define these three splits?</summary>
     
     Note: these three sets should be _disjoint_ (i.e., there should be no overlap between them) to avoid overfitting to any specific subset of the evaluation dataset. Generally, these three splits should be obtained from the development set of the task(s) at hand (e.g., the "Cyber dev set"). I should _not_ look at the test set (e.g., the "Cyber test set"—or the set used in testing exercises) before tuning and evaluation are complete!
</details>

- [ ] I have checked with [#ru-elicitation](https://aisecurityinstitute.slack.com/archives/C06HFEN9RH6) and [#soe-general](https://aisecurityinstitute.slack.com/archives/C07SW4U3GCR) that my experimental design is valid.
     <details>
      <summary>What should I ask about and why?</summary>
     It is recommended to post experimental plans in [#ru-elicitation](https://aisecurityinstitute.slack.com/archives/C06HFEN9RH6) _before_ starting with elictation experiments. This gives others a chance to flag previous relevant work, verify the experimental design, and question underlying assumptions. If I am especially unsure about experimental design (e.g., data splits, amount of repeats) and statistical analysis of the results, I can post in [#soe-general](https://aisecurityinstitute.slack.com/archives/C07SW4U3GCR).
</details>

## Eval logs

Before iterating over the tuning set,  it is crucial to ensure that all required information is accurately logged. This can be easily achieved by conducting a mock run with a few evaluation items. In particular:

- [ ] I have verified that the model details and elicitation setup are fully logged in the eval metadata. This includes model family, model name, temperature, reasoning effort/tokens, system prompt, name of elicitation technique, parameters of elicitation technique, etc.—*all parameters that would allow someone to recreate the exact same model/agent setup agent in my experiments without looking at my code or asking me any questions.*
- [ ] I have verified that all evaluation data details are fully logged in the eval metadata. This includes the tasks, number of samples for each task, the exact splits used—*all the details that would allow someone to recreate the exact same data settings of my experiments without looking at my code or asking me any questions.*
- [ ] I have verified that eval logs are stored in the intended repository. 
     <details>
      <summary>What is the correct repository/folder to store eval?</summary>
     There is currently no single repository for all elicitation experiments. Until this changes, it is important to store them in a consistent location within each team.
</details>

## Reporting
<details>
<summary>How does a good report look like?</summary>
     A good report includes a clear and intuitive explanation of the proposed elicitation method, ideally accompanied by a visual sketch. It should detail the components of the experimental setup, such as evaluation tasks, base models, and data splits, along with an accurate description of the baselines used for comparison. The report should present the results of the proposed elicitation approach against the baseline on the Evaluation set and include uncertainty estimates wherever possible. Additionally, a qualitative analysis focusing on error cases and instances of improved performance over the baseline should be provided. The report should be well-organized and span 2-4 pages, plus an appendix. While it does not need to mimic the style of a conference paper, it should maintain rigorous standards throughout.
</details>   
<!-- - [ ] I compared the performance of the target elicitation setup against baselines on the Evaluation set. -->

- [ ] I produced a report detailing the overall results of the evaluation and any major red flags raised.
- [ ] I uploaded it to the <a href="https://beisgov.sharepoint.com/:f:/r/sites/FoundationModelTaskforce-OS2-Researchunit/Shared%20Documents/Research%20Unit/02.%20Workstreams/8.%20Platform/7.%20Capability%20Elicitation/Projects%20-%20Summaries?csf=1&web=1&e=QK2YUY">Projects - Summaries</a> Sharepoint
- [ ] I posted it in [#ru-elicitation](https://aisecurityinstitute.slack.com/archives/C06HFEN9RH6) 

      
