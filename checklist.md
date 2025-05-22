# Elicitation Checklist 

🔴 High Priority 🟠 Medium Priority 🟢 Low Priority

## Experimental setup 

- [ ] I have set a compute budget for this elicitation experiment.
     <details>
    <summary>What is a reasonable amount?</summary>
    Considering that, in typical testing exercises, we have X-Y tokens available, running a single elicitation approach on Cybench should consume no more than X/3 tokens to ensure usability."
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
- [ ] I have identified a development and a test set for the experiments.
  - [ ] I am holding out 1-3 examples from the development set for manual experimentation and I’m not using these to compute dev set results.
  - [ ] For preliminary elicitation experiments, I am only iterating over the development set.
  - [ ] I do not look at the test set before all iterations are complete.
- [ ] I have checked with [#soe-general](https://aisecurityinstitute.slack.com/archives/C07SW4U3GCR) and [#ru-elicitation](https://aisecurityinstitute.slack.com/archives/C06HFEN9RH6) that my experimental design is valid. 
  - [ ] For confirmatory elicitation experiments, I am additionally iterating over a held-out portion of the test set. 
  - [ ] My evaluation has sufficient statistical power to distinguish between current setup and other setups / human experts. 

