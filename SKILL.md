---
name: homework-grader
description: Grade student homework/assignment images with AI vision. Supports math, multiple choice, fill-in-blank, true/false, short answer, and matching exercises. Use when receiving images of student work that needs correctness marking and score computation. Triggers on homework photos, scanned assignments, worksheet images, or exam papers.
---

# Homework Grader

## Overview

Grade student homework from images. For each assignment image received, analyze the content, identify questions and student answers, mark correct/incorrect, and produce a structured score report.

Supports these assignment types:
- **Math**: Arithmetic, algebra, geometry, word problems
- **Multiple choice**: Single-answer and multi-select
- **Fill-in-the-blank**: Single words, phrases, or short responses
- **True/False**: Statement verification
- **Short answer**: Written responses that need fact-checking
- **Matching**: Connecting related items
- **Mixed**: Any combination of the above

## Workflow

### Step 1: Understand the Assignment

Read the image(s) and identify:

1. **Total questions** — Count all questions, sub-questions, or items
2. **Question types** — Categorize each (math, multiple choice, etc.)
3. **Answer key** (if provided) — Look for a separate answer key image or text. If none, use your own knowledge for correctness (especially for math)
4. **Point values** — Note if questions have different weightings
5. **Instructions** — Note any special instructions ("show your work", "circle the answer")

### Step 2: Grade Each Question

For each question:

1. **Read the student's answer** from the image
2. **Determine correctness**:
   - If answer key exists: compare directly
   - Math problems: work through the calculation yourself
   - Factual questions: use your knowledge
   - Subjective/short answer: use reasonable judgment
3. **Award partial credit** where appropriate (show your work, partial match)
4. **Provide brief feedback** on wrong answers (correct answer, why it's wrong)

### Step 3: Compute Score

1. Sum points earned across all questions
2. Calculate percentage: `(points earned / total possible points) × 100`
3. If no explicit point values, treat each question as 1 point

### Step 4: Output Report

Structure your response with:

```
## 批改结果

### 逐题批改
1. ❌ [题目内容] — 学生答案: X → 正确答案: Y [简评]
2. ✅ [题目内容] — [可选备注]
3. ⚠️ [题目内容] — 部分正确 [说明]

### 总分
**X / Y (Z%)**

### 评语（可选）
[总结性评语，鼓励为主]
```

### Step 5: Provide Image Description (for Reference)

After grading, if helpful, give a brief text transcription of what you saw in the image so the user can verify accuracy.

## Grading Guidelines by Question Type

### Math Problems
- Solve the problem yourself, don't just trust the student's answer
- Partial credit for correct process with arithmetic mistake: ½ or ¾ credit
- Show the correct solution briefly for wrong answers

### Multiple Choice
- Must match exactly to the answer key
- Single-answer: 1 if correct, 0 if wrong
- Multi-select: all must match for full credit

### Fill-in-the-Blank
- Be lenient with spelling for younger students unless the subject demands precision
- Case-insensitive matching unless it matters (e.g., proper nouns, programming)

### Short Answer
- Judge for factual accuracy and completeness
- Award partial credit for partially correct answers
- Be generous with younger students, stricter with older ones

### True/False
- Exact match to answer key

### Matching
- Each match counted as a separate question
- One point per correct match

## When No Answer Key Is Provided

- **Math**: Solve it yourself — this is the most reliable approach
- **Factual questions**: Answer from your own knowledge
- **Subjective/opinion questions**: Grade for reasoning, not just the "right" answer
- **If unsure**: Flag as uncertain and suggest the user provide an answer key

## Academic Integrity Note

If the student's answers appear possibly copied or suspicious (identical wrong answers across students, unusually advanced vocabulary, etc.), mention it gently in the feedback without accusations.

## Output Language

Use the same language as the user's message. If the user writes in Chinese, respond in Chinese. Default to Chinese if unsure.
