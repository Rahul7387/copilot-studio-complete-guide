# Evaluation — Deep Dive

Evaluation is Copilot Studio's built-in QA system. Create test sets and run them systematically against your agent.

## Where: Agent → Evaluation

## Core concepts
| Concept | Description |
|---|---|
| Test set | Collection of test cases |
| Test case | One question + expected answer |
| Evaluation run | Running a test set against current agent version |
| Pass / Fail | Whether agent's response matches expected |
| Score | % of test cases that passed |

## 4 ways to create test sets
1. Auto-generate — Copilot Studio generates from existing topics/knowledge
2. CSV import — Upload spreadsheet of questions and expected answers
3. Test canvas capture — Save conversations from test panel
4. Manual entry — Add cases one by one

## CSV format
question,expected_answer,category,priority
"How do I reset my password?","Visit aka.ms/sspr...","password","high"

## When to run evaluations
- After every instruction change
- After adding new knowledge sources
- After updating topics
- Before every production release

## Targets
- 90%+ pass rate before publishing
- Review failed cases — use them to improve instructions/knowledge
