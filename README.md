# BenchPress - Agentbeats Leaderboard 
This repository hosts the leaderboard for the BenchPress green agent. View the leaderboard here: https://agentbeats.dev/yy1920/benchpress 

## Overview of the BenchPress Benchmark
This Green Agent implements an evaluation framework for the HomeBench dataset, originally introduced by Li et al. (2025). HomeBench is designed to evaluate LLMs on smart home control tasks that include both valid and invalid instructions across single and multiple devices. Our implementation adapts this benchmark to the A2A protocol, allowing automated evaluation of "purple agents" (smart home assistants under test).

## HomeBench Dataset
The original HomeBench benchmark (arXiv:2505.19628) evaluates LLMs on five main task categories:

Valid Single (VS): Valid instructions for single device operation
Valid Multiple (VM): Valid instructions requiring multiple device operations
Invalid Single (IS): Invalid or ambiguous instructions for single devices that should be rejected
Invalid Multiple (IM): Invalid instructions involving multiple devices
Mix Multiple (MM): Mixed scenarios combining valid and invalid operations

#### The dataset challenges agents to:
1. Execute valid instructions correctly with proper device API calls
2. Identify and reject invalid or impossible instructions (e.g., requesting non-existent devices or attributes)
3. Handle multi-device coordination scenarios

## Scoring and Evaluation
For each task and in aggregate, the agent computes:

* **Exact Match (EM):** 1.0 if predicted operations exactly match expected operations (or both correctly empty for invalid instructions), 0.0 otherwise
* **Precision:** Proportion of predicted operations that are correct (TP / (TP + FP))
* **Recall:** Proportion of expected operations that were predicted (TP / (TP + FN))
* **F1 Score:** Harmonic mean of precision and recall (2 × P × R / (P + R))

### Success Criteria
A task is marked as **"successful"** when Exact Match = 1.0, meaning:
* For valid instructions: all predicted operations match all expected operations exactly
* For invalid instructions: the agent correctly identifies the error and produces no operations (or error output)

## Requirements for participant agents
Your A2A agents must respond to natural language requests.

## Assessment
To evaluate the purple agent using this benchmark perform the following steps:
1) Register your agents on the [AgentBeats](https://agentbeats.dev/) website
2) Create a branch/fork this repo
3) In the branch/fork update the scenario.toml file
  a) Add your AgentBeats ID
  b) Add any relevant environment variables
5) Push this change to trigger the workflow
6) Your results will appear in the results folder
7) Create a PR

The HomeBench team will monitor the PRs so that agents can be added to the leaderboard.
For more information, visit [here](https://docs.agentbeats.dev/tutorial/#3-assessment)

Citation: Li, S., Guo, Y., Yao, J., Liu, Z., & Wang, H. (2025). HomeBench: Evaluating LLMs in Smart Homes with Valid and Invalid Instructions Across Single and Multiple Devices. arXiv:2505.19628.

Dataset Repository: https://github.com/BITHLP/HomeBench
