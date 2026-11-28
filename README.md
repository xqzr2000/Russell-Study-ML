# Russell Studies Machine Learning

This repository collects my machine learning study notebooks, progress, and reflections. [View my project portfolio](https://github.com/xqzr2000)

## Study notes

- [Math for data science](Math4DS_Notes_Done.ipynb)
- [Math for machine learning](Math4ML_Notes_Done.ipynb)
- [APM notes](APM_Notes_on_Pause.ipynb)
- [Token Monster](Token_Monster_Notes_first_half.ipynb)
- [Understanding Mario](understanding_Mario_first_half.ipynb)

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

**1. Flagship: a data-analysis agent on a public benchmark.** This fills gaps 1 and 2 and reuses what I have: the A1 harness, the A2 evaluation skills, and the cloud setup. The agent is the data scientist in [Russell's BaseAgent](https://github.com/xqzr2000/Russells_BaseAgent), coordinated by Jack. Two targets:
- **DABStep (committed):** a multistep data-analysis agent benchmark with 450 questions in easy and hard settings. It tests multi-step reasoning over mixed inputs: unstructured documents, lookup tables, and schema metadata. Iterate on the dev split locally, then submit to the leaderboard.
- **Spider 2.0-Lite (flex):** a text-to-SQL benchmark with 547 realistic examples across BigQuery, Snowflake, and SQLite databases. Only the SQLite part (135 examples), so no cloud warehouse accounts are needed. Retrieval comes in naturally, because the agent has to find the right tables and columns. If time runs short, this is the first thing to shrink.

**2. Kaggle: one Playground Series competition.** Kaggle is the reputation a data science major is expected to have, so it stays in the plan. One live tabular competition with a real leaderboard, done well: a fixed CV split, a baseline, one idea per experiment with its CV score, and a final submission. The same agent does it with me (it runs the stages, I review and submit by hand), so it also tests the harness on a classic DS task before the benchmarks. It comes after the card-classifier task in BaseAgent, a Kaggle image dataset that I used to build up the agent's harness.

**3. CMU 17-645, Machine Learning in Production.** This fills gap 3.
- It covers building, deploying, assuring, and maintaining software products with machine-learned models, from classic ML to LLMs to AI agents. Slides and assignments are on GitHub under a Creative Commons license.
- Relevant pieces: Lab 07 (Agents and MCP), I3 (MCP and Security), Lab 08 (Prometheus and Grafana) and M3 (Monitoring and CD).
- A/B testing isn't an assignment topic there, but a lecture covers it.

Plan: deploy the data agent from project 1, monitor it, and run my own A/B test of two harness versions on the same DABStep questions. The deployed agent is also Jack at his public URL.

**4. Optional: CS336 Assignment 5.** It rounds out post-training: supervised fine-tuning, expert iteration, GRPO and variants, RL on Qwen 2.5 Math 1.5B to improve MATH, plus an optional Part 2 on safety alignment such as DPO. It overlaps a lot with A3's GRPO, so only if there's time.

Considered and not used: Stanford CS329Z covers RAG, memory and multi-agent systems, but only the assignment descriptions are public; the starter code is not.

Parked (July–August buffer or later): a chemistry dataset challenge, more Kaggle competitions, and a 17-645 course-pack pilot (Jack learning the course as skills).

## 2. Order to fall 2027

About 30 weeks × 3 hours ≈ 90 hours of BaseAgent sessions to June 30. Two sessions a week go to the current task, one to my self-interview or to checking BaseAgent changes.

| Dates | Task | Weeks | Status |
| --- | --- | --- | --- |
| Now (weeks) | Finish the 124M model and SST-5, rework the three 11-768 notebooks, build the cloud-walker notebook | — | committed |
| Nov 30 – Dec 13 | Close the card-classifier task: last harness fixes, one confirming run, its `showcase/` folder | 2 | committed |
| Dec 14 – Jan 24 | Kaggle Playground Series (the tabular episode open then). Over the holidays the agent's benchmark batch runner gets built | 6 | committed |
| Jan 25 – Mar 28 | DABStep: dev baseline → failure categories → skills → harness v2 → leaderboard submission | 9 | committed |
| Mar 29 – May 2 | Spider 2.0-Lite, SQLite part | 5 | flex |
| May 3 – Jun 30 | Deploy, monitor and A/B test (MLIP materials); Jack's recruiter side; public URL by June 30 | 8 | committed |
| Jul – Aug | Buffer, public posts and a portfolio pass, before applications open | — | |

Every task gets its own folder in [`showcase/`](https://github.com/xqzr2000/Russells_BaseAgent) in the BaseAgent repo: what the task was, what we built so the agent could do it, and the results, with a build log that links them all.

---

## 3. "No, seriously, did you write the code?"

Writing the core functions by hand would turn a six-week tour of the LLM and agent stack into six months on two or three functions. For a data science major aiming at a "do-it-all" role, **breadth plus judgement** beats being able to rebuild a GRPO trainer from memory. My TypeScript experience taught the same lesson: when I write everything myself in an unfamiliar area, one blocker stops the whole project.

The important part:

> The issue isn't who types the code. **It's whether anything proves I understood it.**

I start and drive these projects, and I go back and forth with the agent a lot and do plenty of editing myself (the commit history in each repo shows it). But the agent writes most of the code and the explanations. So the fix isn't "write it yourself." It's **checking my understanding in ways that don't involve writing code**: the Predict, Work-it-by-hand and In-my-words cells in each companion notebook. For the agent work, the proof is `showcase/` in BaseAgent: for each task, what broke, what I decided to change and why, and how I measured whether it helped.

### Where writing code myself still matters

- **Data science interviews.** These usually include live SQL, pandas and statistics with no AI help. That's my home domain, it's tested directly, and it's where getting stuck would cost me an offer. A small separate practice track, 20–30 minutes a few times a week, does more for the hiring goal than hand-writing LLM code.
- **Debugging when the agent goes in circles.** I've done this well already: I caught the dead-server retry loop in A1 and the stalls in A3. Reading code and diagnosing failures is part of the whole project experience.

The split: **agents write the LLM and agent code, I own the decisions and the checks, and I keep my data science fundamentals sharp by hand.** That's the do-it-all profile: I design the experiments and judge the results, and agents build what I specify.
