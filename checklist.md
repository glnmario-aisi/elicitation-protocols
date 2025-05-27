# Elicitation Checklist 

🔴 High Priority 🟠 Medium Priority 🟢 Low Priority

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
      
  - If you are testing a new technique (e.g., a new tool) or conducting a grid search over parameters (e.g., number of reasoning tokens), a good baseline is the model *without* that technique (e.g., without the tool, or with reasoning off).
  - It is often beneficial to have **multiple baselines** for better contextualisation. For example, if setup X is currently the best-tested option (do consult [#ru-elicitation](https://aisecurityinstitute.slack.com/archives/C06HFEN9RH6) and the <a href="https://beisgov.sharepoint.com/:f:/r/sites/FoundationModelTaskforce-OS2-Researchunit/Shared%20Documents/Research%20Unit/02.%20Workstreams/8.%20Platform/7.%20Capability%20Elicitation/Projects%20-%20Summaries?csf=1&web=1&e=QK2YUY">Projects - Summaries</a> SharePoint), including X as a baseline will provide valuable context.
  - If you are unsure, it might be a good idea to post a question in [#ru-elicitation](https://aisecurityinstitute.slack.com/archives/C06HFEN9RH6).
  </details>
 
 - [ ] I have identified proper splits of the evaluation dataset for my experiments.
     - **Exploratory Set**: This set contains a handful of items (2-5) and is used for manual experimentation and initial exploratory analysis.
     - **Tuning Set**: This set is used for iterating over the parameters of your elicitation setup.
     - **Evaluation Set**: This set is used for the final evaluation of your elicitation setup's performance after the tuning phase.
     <details>
     <summary>How to define these three splits?</summary>
     
     Note that these three sets should be _disjoint_, i.e., there should be no overlap between them. Generally, you should obtain these three splits from the development set of the task(s) at hand (e.g., the "Cyber dev set"). You should _not_ look at the test set (e.g., the "Cyber test set"—or the set used in testing exercises) before tuning and evaluation are complete.
</details>

- [ ] I have checked with [#ru-elicitation](https://aisecurityinstitute.slack.com/archives/C06HFEN9RH6) and [#soe-general](https://aisecurityinstitute.slack.com/archives/C07SW4U3GCR) that my experimental design is valid.
     <details>
      <summary>Why?</summary>
     It is recommended to post your experimental plan in [#ru-elicitation](https://aisecurityinstitute.slack.com/archives/C06HFEN9RH6) _before_ starting with your elictation experiments. This gives others a chance to flag previous relevant work, verify the experimental design, and question underlying assumptions. If you are particularly unsure about experimental design (e.g., data splits, amount of repeats) and statistical analysis of the results, also post in [#soe-general](https://aisecurityinstitute.slack.com/archives/C07SW4U3GCR).
