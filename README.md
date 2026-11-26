# Russell Studies Machine Learning

I’m Russell, a data science student at Pitt. I’m interested in designing experiments and building agents that gather and analyze data. This README is the starting point for my GitHub projects, results, and study notes.

[Current work](#current-work-and-whats-next) · [Learning gaps](#1-what-im-missing) · [Reflection on AI-assisted development](#3-no-seriously-did-you-write-the-code)

## Applied data science

- **Data-visualization agent evaluation (CMU 11-768 A2).** In this independent course adaptation, I used human labels and an error taxonomy to diagnose the evaluator’s mistakes. The final evaluator scored 0.8726 macro-MCC on 110 public seed runs, up from 0.5235 at baseline. [Repository](https://github.com/xqzr2000/cmu-11-768-assignment-2) · [Final report](https://github.com/xqzr2000/cmu-11-768-assignment-2/blob/main/report.pdf) · [Walkthrough](https://github.com/xqzr2000/cmu-11-768-assignment-2/blob/main/notebooks/CMU_11_768_Assignment_2_Project_Walkthrough.ipynb)
- **YouTube-SideKick.** A recommendation engine with hand-labeled data, offline ranking experiments, and a Chrome side panel. In a seven-video comparison, 66% of SideKick’s top-ten suggestions and 49% of YouTube’s were labeled good. [Repository](https://github.com/xqzr2000/YouTube-SideKick) · [Ranking experiments](https://github.com/xqzr2000/YouTube-SideKick/blob/main/reports/E4-ranker.md)
- **Russell’s Scout.** A scheduled pipeline that collects, deduplicates, and scores Vancouver job postings and stores them in PostgreSQL. It completed 14 sweeps, seven digests, and seven backups in a week of unattended operation. [Repository](https://github.com/xqzr2000/russells-scout) · [Walkthrough](https://github.com/xqzr2000/russells-scout/blob/main/notebooks/Russells_Scout_Project_Walkthrough.ipynb) · [Run results](https://github.com/xqzr2000/russells-scout/blob/main/docs/phase2-results.md)

## Current work and what's next

- I’m finishing the 124.7M-parameter language model and the SST-5 sentiment experiment. I’m also reworking the three CMU 11-768 walkthrough notebooks, starting with A2, and adding the cloud-walker notebook. The GPT-2 XL-scale run is on hold.
- My next project is a data-analysis agent that can find relevant information and answer questions about real datasets. I’m considering DABStep and the SQLite tasks in Spider 2.0-Lite, with deployment, monitoring, and an A/B test of two harness versions to follow.

## Agent systems and model training

- **Russell’s BaseAgent.** A reusable Python ReAct framework with a data science agent that explores CSVs in Jupyter and returns a summary and a runnable notebook. [Repository](https://github.com/xqzr2000/Russells_BaseAgent)
- **Agent harness (CMU 11-768 A1).** An independent course adaptation using a Docker sandbox to study tool design, context compaction, and token usage. [Repository](https://github.com/xqzr2000/cmu-11-768-assignment-1)
- **Language modeling from scratch (CS336 adaptation).** I trained a 22.7M-parameter Transformer on TinyStories and completed the first training stage of a 124.7M-parameter Llama-style model on FineWeb-Edu. [Repository](https://github.com/xqzr2000/Stanford-CS336-Llama-Adaptation) · [Training results](https://github.com/xqzr2000/Stanford-CS336-Llama-Adaptation/blob/main/CS336_Colab/README.md)
- **Agent reinforcement learning (CMU 11-768 A3).** An independent course adaptation that post-trained Qwen3.5-4B on Modal H100s. On 50 TextCraft tasks, pass@4 went from 14% for the base model to 68% for the step-41 adapter. [Repository](https://github.com/xqzr2000/cmu-11-768-assignment-3) · [Final report](https://github.com/xqzr2000/cmu-11-768-assignment-3/blob/main/docs/Report.md)
- **Mario Ops.** Cloud experiments with Double DQN in Colab, Codespaces, and AWS, plus a vision model that plays from screenshots. [Repository](https://github.com/xqzr2000/Mario_Ops)

## Product prototypes

- **WiseShelf.** A Pitt Blitz prototype for a unified shopping cart with AI-assisted budgeting. [Repository and demo](https://github.com/xqzr2000/Side_Cart_Blitz)
- **SideBuySide.** A Chrome side-panel shopping shelf that collects product cards from retailer pages. [Repository and demo](https://github.com/xqzr2000/SideBuySide_Blitz)
- **Vibe Coded Shopper.** A terminal-based shopping group chat that experiments with different agent personalities. [Repository](https://github.com/xqzr2000/Vibe_Coded_Shopper)
- **Focus Room.** An educational two-agent chat prototype for ADHD screening conversations and researching attention-training resources. [Repository](https://github.com/xqzr2000/Vibe_Coded_ADHD_Game_Room)

## Study notes

This repository also contains my notebook-based study notes. [Math for data science](Math4DS_Notes_Done.ipynb) · [Math for machine learning](Math4ML_Notes_Done.ipynb) · [APM notes](APM_Notes_on_Pause.ipynb) · [Token Monster](Token_Monster_Notes_first_half.ipynb) · [Understanding Mario](understanding_Mario_first_half.ipynb)

---

> Agent, please keep me on a plan!

## 0. On my deck (Nov-24-2026)

- Finish the 124M model and SST-5; park GPT-2 XL.
- Rework the three 11-768 walkthrough notebooks, starting with A2 (it asks nothing of the reader yet, and A2 is my strongest data science story), and add a cloud-walker notebook.

---

## 1. What I'm missing

My four projects cover how an LLM is **made** (pretraining), **driven** (harness), **judged** (evaluation) and **improved** (RL post-training). Measured against my target role (look at a business, design experiments, build agents that gather and analyze data, deliver insight), three gaps stand out:

1. **Data, oddly enough.** None of the four projects works on a database, a warehouse or a business question. For a "data scientist who builds agents," this is the largest gap. It's also where my lab experience (instrument data → SQL → LIMS) becomes a story only I can tell.
2. **Retrieval and memory.** None of them does RAG, embeddings or search. Most real agents need to find information before they reason over it.
3. **Production.** I've used Docker and Modal, but haven't deployed a service, monitored it, or run an A/B test on it. A/B testing especially is core data science, and interviewers will ask about it.

Lower priority: supervised fine-tuning or DPO (A3 used RL only), and multi-agent frameworks or MCP.

### Assignments and projects that fill them

**1. Flagship: a data-analysis agent on a public benchmark.** This fills gaps 1 and 2 and reuses what I have: the A1 harness, the A2 evaluation skills, and the cloud setup. Two good targets:
- **DABStep:** a multistep data-analysis agent benchmark with 450 questions in easy and hard settings. It tests multi-step reasoning over mixed inputs: unstructured documents, lookup tables, and schema metadata.
- **Spider 2.0-Lite:** a text-to-SQL benchmark with 547 realistic examples across BigQuery, Snowflake, and SQLite databases. Start with the SQLite part so no cloud warehouse accounts are needed. Retrieval comes in naturally, because the agent has to find the right tables and columns.

**2. CMU 17-645, Machine Learning in Production.** This fills gap 3.
- It covers building, deploying, assuring, and maintaining software products with machine-learned models, from classic ML to LLMs to AI agents. Slides and assignments are on GitHub under a Creative Commons license.
- Relevant pieces: Lab 07 (Agents and MCP), I3 (MCP and Security), Lab 08 (Prometheus and Grafana) and M3 (Monitoring and CD).
- A/B testing isn't an assignment topic there, but a lecture covers it.

Plan: deploy the data agent from project 1, monitor it, and run my own A/B test of two harness versions.

**3. Optional: CS336 Assignment 5.** It rounds out post-training: supervised fine-tuning, expert iteration, GRPO and variants, RL on Qwen 2.5 Math 1.5B to improve MATH, plus an optional Part 2 on safety alignment such as DPO. It overlaps a lot with A3's GRPO, so only if there's time.

Considered and not used: Stanford CS329Z covers RAG, memory and multi-agent systems, but only the assignment descriptions are public; the starter code is not.

## 2. Order to fall 2027

1. **Now (weeks):** finish the 124M model and SST-5, rework the three 11-768 notebooks, build the cloud-walker notebook.
2. **Winter to spring:** the data-agent flagship.
3. **Spring to summer:** deploy, monitor and A/B test it, using the MLIP materials.
4. **Summer:** the public posts plus a portfolio pass, before applications open.

---

## 3. "No, seriously, did you write the code?"

Writing the core functions by hand would turn a six-week tour of the LLM and agent stack into six months on two or three functions. For a data science major aiming at a "do-it-all" role, **breadth plus judgement** beats being able to rebuild a GRPO trainer from memory. My TypeScript experience taught the same lesson: when I write everything myself in an unfamiliar area, one blocker stops the whole project.

The important part:

> The issue isn't who types the code. **It's whether anything proves I understood it.**

I start and drive these projects, and I go back and forth with the agent a lot and do plenty of editing myself (the commit history in each repo shows it). But the agent writes most of the code and the explanations. So the fix isn't "write it yourself." It's **checking my understanding in ways that don't involve writing code**: the Predict, Work-it-by-hand and In-my-words cells in each companion notebook.

### Where writing code myself still matters

- **Data science interviews.** These usually include live SQL, pandas and statistics with no AI help. That's my home domain, it's tested directly, and it's where getting stuck would cost me an offer. A small separate practice track, 20–30 minutes a few times a week, does more for the hiring goal than hand-writing LLM code.
- **Debugging when the agent goes in circles.** I've done this well already: I caught the dead-server retry loop in A1 and the stalls in A3. Reading code and diagnosing failures is part of the whole project experience.

The split: **agents write the LLM and agent code, I own the decisions and the checks, and I keep my data science fundamentals sharp by hand.** That's the do-it-all profile: I design the experiments and judge the results, and agents build what I specify.
