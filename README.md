# verbis-graph-investigator

Verbis Graph Investigator
AI diligence agent concept for investors and venture funds, built on top of Verbis Graph as the knowledge retrieval, ontology, and multi-hop reasoning layer.
What this repository is
This repository is a hackathon review package for the Google for Startups AI Agents Challenge.
It is designed to be reviewer-friendly and honest about current status:
Already implemented foundation: Verbis Graph as the graph-based knowledge layer
Proposed challenge workflow: Verbis Graph Investigator as the agent layer for investment diligence
Included here: architecture, API scaffold, agent workflow skeleton, mock tools, and sample outputs
Not included here: proprietary production internals of Verbis Graph
Core idea
Instead of only chatting over documents, Verbis Graph Investigator turns a startup data room into an evidence-backed diligence workflow.
The agent:
receives a diligence task
queries Verbis Graph for entities, relationships, supporting evidence, and contradictions
classifies risks and missing evidence
drafts a diligence memo with citations
Why Verbis Graph matters
Verbis Graph is used as the system's core layer for:
knowledge retrieval
ontology mapping
graph memory
evidence linking
multi-hop reasoning
source grounding
Repository structure
```text
app/
  api/
    main.py                FastAPI entrypoint
  agents/
    planner.py             Creates investigation plan
    evidence.py            Retrieves supporting/contradicting evidence
    risk.py                Scores findings by category
    memo.py                Drafts a diligence memo
  services/
    orchestrator.py        End-to-end workflow orchestration
    verbis_graph_client.py Verbis Graph adapter (mocked)
  schemas/
    models.py              Shared request/response models
docs/
  submission_notes.md      Suggested Devpost/judge explanation
requirements.txt
Dockerfile
.env.example
```
Quick start
```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
uvicorn app.api.main:app --reload
```
Open:
`GET /health`
`POST /investigate`
`GET /sample-report`
Example request
```json
{
  "workspace_id": "demo-startup-dataroom",
  "goal": "Prepare an investment diligence memo",
  "focus_areas": ["revenue support", "contract obligations", "missing evidence"]
}
```
Positioning statement
Verbis Graph Investigator is an AI diligence agent that uses Verbis Graph as its retrieval, ontology, and multi-hop reasoning layer to turn startup data rooms into evidence-backed investment memos.
Notes for reviewers
This repo is intended for challenge review and architecture evaluation. It demonstrates how the agent workflow is structured around Verbis Graph, without exposing proprietary internal product code.
