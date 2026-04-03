# Submission Summary

## Team
**Team Name:** SEENUX VERSION
**Members:** [Insert Your Name] | AI Architect
[Insert Member Name] | Workflow Engineer
[Insert Member Name] | Documentation Lead
**Contact Email:** [Insert Your Email]

---

## Problem Statement
**Selected Problem:** PS-01
**Problem Title:** Client Onboarding

This system addresses the 50% error rate and 45-minute manual bottleneck in the Scrollhouse onboarding process. By automating data flow across Airtable, Notion, and Google Drive, the system eliminates disorganized handovers and ensures that billing and project structures are 100% accurate from day one, protecting client trust and agency cash flow.

---

## System Overview
The Scrollhouse Autopilot System (SAS) is an agentic workflow that manages the end-to-end client setup. Upon a CRM trigger, the system validates brand data, creates a structured Google Drive environment, clones a live Notion template, and populates Airtable. Unlike static automation, it uses an LLM-driven supervisor to resolve naming conflicts, handle API retries, and generate a proactive content strategy for the client's first month.

---

## Tools and Technologies

| Tool or Technology | Version or Provider | What It Does in Your System |
|---|---|---|
| Gemini 1.5 Pro | Google AI Studio | The core reasoning engine for edge-case handling and content generation. |
| LangGraph | LangChain | Orchestration framework for stateful, cyclic agent workflows. |
| n8n | Railway | Integration layer connecting Google Drive, Notion, and Airtable APIs. |
| Pinecone | Vector Database | Stores master template metadata and brand guidelines for RAG retrieval. |
| Airtable API | REST | Primary database for tracking client records and project links. |

---

## LLM Usage
**Model(s) used:** Gemini 1.5 Pro
**Provider(s):** Google
**Access method:** API Key

| Step | LLM Input | LLM Output | Effect on System |
|---|---|---|---|
| Intake Validation | Raw CRM Form Data | JSON / Error Flags | Identifies typos in AM names or duplicate brands before data entry. |
| Content Strategy | Brand Category | 5-Pillar Strategy | Injects custom creative ideas into the new Notion Client Hub. |
| Self-Healing | API Error Logs | Retry/Alert Decision | Determines if a failure is a transient glitch (retry) or a fatal error (alert). |

---

## Algorithms and Logic
The system utilizes **LangGraph** to maintain a persistent state during the onboarding mission.
- **Fuzzy Matching:** We use the LLM to perform semantic searches in Airtable to detect "GlowSkin" vs "Glow Skin Co" as potential duplicates.
- **Dynamic RAG:** The agent queries a vector store to find the most recent "Master Template" ID in Notion, ensuring the system never uses an outdated layout.
- **Exponential Backoff:** Custom logic handles Google Drive API rate limits by intelligently spacing out retry attempts.

---

## Deterministic vs Agentic Breakdown

**Estimated breakdown:**

| Layer | Percentage | Description |
|---|---|---|
| Deterministic automation | 40% | Webhook triggers, folder hierarchy creation, and basic API data mapping. |
| LLM-driven and agentic | 60% | Duplicate reasoning, personalized content generation, and autonomous error recovery. |

**Total: 100%**

The agentic layer allows for "human-like" decision making. Without the LLM, the system would fail on simple typos or create duplicate folders for existing clients, requiring constant manual cleanup.

---

## Edge Cases Handled

| Edge Case | How Your System Handles It |
|---|---|
| Duplicate Brand Name | Agent pauses the flow and requests AM confirmation if a similar name exists. |
| API Failure | The Auditor agent attempts a 3-stage retry before notifying the human manager. |
| Unrecognized AM | Maps the input to the closest matching verified staff member in the database. |

---

## Repository
**GitHub Repository Link:** [PASTE YOUR FORK LINK HERE]
**Branch submitted:** main
**Commit timestamp of final submission:** [PASTE YOUR COMMIT HASH HERE] 2026-04-03 13:20 UTC

---

## Deployment
**Is your system deployed?** Yes
**Deployment link:** https://seenux-repo-onboarding.railway.app
**Platform used:** Railway
**What can be tested at the link:** Live n8n workflow logs and the real-time onboarding success dashboard.

---

## Known Limitations
The system currently does not automatically "Rollback" created folders if the final email fails; this is a planned safety feature for the next iteration.

---

## Anything Else
The "SEENUX VERSION" system adds a "Value-First" layer by generating five custom video hooks for the client's niche as part of the initial Notion setup.
