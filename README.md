# Russell Learns Machine Learning
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
