# Prompt Engineering Patterns — Scratch Doc
### B.Tech CSE | Placement Prep Context

---

## Pattern 1 — PERSONA

### The Prompt

> "You are a senior placement coach at Aditya University. You have prepared 200 B.Tech CSE students for TCS, Infosys, and Cognizant placement interviews. A 3rd-year CSE student with 7.5 CGPA asks you about Big-O notation. Explain it the way you would in a 1-on-1 prep session — concrete, conversational, exam-relevant."

---

### Claude's Response

**What Is Big-O, Really?**

Big-O tells you how your code's performance scales as the input gets bigger — not what it does on 10 elements, but on a million elements. That's it. Everything else follows from that.

---

**The Friend-List Analogy**

Imagine you're looking for a friend's name in a list:

- **O(1)** — You already know their position. You go directly there. Doesn't matter if the list has 10 names or 10 crore names. Same effort. *(HashMap lookup, direct array access)*
- **O(log n)** — The list is sorted. You open the middle, check if the name is before or after, then eliminate half. Repeat. 1 crore names? About 23 checks. *(Binary search, balanced BST)*
- **O(n)** — You check every name, one by one. Twice as many names = twice as long. *(Linear search, single loops)*
- **O(n log n)** — You divide the list, sort each half, then merge. This is what all good sorting algorithms land on. *(Collections.sort() in Java, sort() in Python)*
- **O(n²)** — You compare every name with every other name. 1000 names? 1 million comparisons. The nested loop trap. *(Bubble sort, selection sort)*
- **O(2ⁿ)** — Each step doubles the work. 30 elements? Over a billion operations. *(Naive recursive Fibonacci)*

---

**What TCS / Infosys / Cognizant Actually Ask**

They rarely ask you to derive Big-O mathematically. What they do is:
1. Show you code and ask "what's the time complexity?"
2. Ask you to optimise a brute-force solution (O(n²) → O(n) using a hashmap)
3. Ask "why is this better than that?"

**How to read code complexity in 3 seconds:**
- One loop over n elements → O(n)
- Loop inside a loop, both over n → O(n²)
- You halve the problem each step → O(log n)
- You loop and halve (like merge sort) → O(n log n)
- Recursive call splits into two sub-calls → O(2ⁿ)

---

**Interview Tip**

When you write code in an interview, say the complexity out loud as you go. Don't wait to be asked. Write a loop, say "this is O(n)." Add a nested loop, say "now we're at O(n²), let me think if there's a better way." Interviewers at TCS and Infosys love this — it shows you're thinking, not just writing.

---

### Score: 5 / 5

**Why:**
- Uses a desi-relevant analogy ("10 crore names") that a 3rd-year student immediately connects with
- Skips theory-first, goes straight to what the actual interview asks
- Gives a concrete 3-second rule for reading code complexity — directly usable in an exam
- Interview narration tip is specific and actionable, not generic advice
- Tone matches a real 1-on-1 session: direct, no padding, no textbook language
- Nothing here would confuse a student with 7.5 CGPA — hits the right difficulty level

**What made the PERSONA pattern work:**
- Naming the exact companies (TCS, Infosys, Cognizant) forced exam-relevant framing
- "200 students" gave the coach credibility, which shifted the tone from textbook to field-tested
- "7.5 CGPA" signalled the student is capable but not advanced — prevented over-explanation and under-explanation equally
- "1-on-1 prep session" unlocked conversational register — no bullet-point overload, no definitions for their own sake

---

---

## Pattern 2 — FEW-SHOT (Example-Driven Format)

### The Prompt

> "Here are example explanations from a placement coach:
>
> Q: What is recursion? A: A function calling itself with a smaller problem. Like Russian dolls — open one, find a smaller one inside. Stops at base case. Example: factorial.
>
> Q: What is a stack? A: LIFO data structure. Push to add, pop to remove. Like a stack of plates — you take from the top.
>
> Q: What is Big-O notation? A:"

---

### Claude's Response

**Q: What is Big-O notation?**

**A:** A way to measure how fast your code grows as input grows. Like a highway — O(1) is a personal jet, O(n) is a car, O(n²) is a bicycle in traffic. Tells the interviewer you think beyond just "does it work." Example: linear search is O(n), binary search is O(log n).

---

### Score: 4 / 5

**Why 4 and not 5:**
- Nailed the format — same length, same structure, same analogy-first style as the examples
- The highway analogy is vivid and original; works well for a student audience
- "Tells the interviewer you think beyond just does it work" — unexpectedly useful framing, not in Pattern 1
- Docked 1 point: the highway analogy slightly obscures *scaling* (the core idea of Big-O) — a jet vs bicycle is about speed, not about *growth rate*. Pattern 1's friend-list analogy was more technically precise

**What made the FEW-SHOT pattern work:**
- The model didn't need to be told "be brief" or "use analogies" — it *inferred* both from the examples
- Two examples was enough to lock in: short answer → analogy → concrete example structure
- Format-matching is the superpower of few-shot: no instructions needed, just show the shape
- Ideal when you want consistent output style across many questions (flashcard sets, glossaries, study notes)

**Pattern 1 vs Pattern 2 — head to head:**

| | PERSONA (P1) | FEW-SHOT (P2) |
|---|---|---|
| Length | Long, thorough | Short, punchy |
| Best for | Deep understanding | Quick recall / flashcards |
| Analogy quality | More precise | More memorable |
| Interview relevance | Explicit | Implied |
| Score | 5/5 | 4/5 |

---

---

## Pattern 3 — CHAIN-OF-THOUGHT

### The Prompt

> "Explain Big-O notation to a placement interview candidate. Think step by step before answering. Step 1: define Big-O in one sentence. Step 2: give one concrete example with code. Step 3: explain why interviewers ask about it. Step 4: synthesise into a 3-sentence summary."

---

### Claude's Response

**Step 1 — Define:** Big-O notation describes how the runtime or space of an algorithm grows relative to its input size.

**Step 2 — Code example:**
```python
# O(n) — one loop
for i in range(n):
    print(i)

# O(n²) — nested loop
for i in range(n):
    for j in range(n):
        print(i, j)
```

**Step 3 — Why interviewers ask:** It reveals whether you can think beyond "does it work" to "does it scale." A solution that works on 100 rows but crashes on 10 million is not production-ready. Interviewers use it to test engineering judgement, not just syntax knowledge.

**Step 4 — Summary:** Big-O measures how an algorithm's performance scales with input size. O(1) is constant, O(n) grows linearly, O(n²) explodes with nested loops. When an interviewer asks for complexity, they want to know: will your code survive real data?

---

### Score: 4 / 5

**Why:**
- The step structure makes reasoning transparent — you can see *why* each claim was made
- Step 3 (why interviewers ask) is the strongest individual insight across all 6 patterns — most students never think about this angle
- Code example is clean, minimal, directly comparable
- Docked 1 point: Step 4 slightly repeats Step 1 rather than truly synthesising. Fix: change the prompt to say "synthesise NEW insight, do not repeat prior steps"

**What made CHAIN-OF-THOUGHT work:**
- Forcing steps before the answer prevents the model from jumping to a generic definition
- Assigning a specific job to each step means nothing is skipped — "why interviewers ask" almost never appears in an unprompted answer
- Best pattern when the *reasoning process* itself is what needs to be taught, not just the answer
- Trade-off: longer output than Few-Shot, but each sentence earns its place

---

## Pattern 4 — STRUCTURED OUTPUT (JSON)

### The Prompt

> "Explain Big-O notation for a placement interview. Return ONLY valid JSON with this exact shape — no markdown fences, no commentary:
> { "definition": "...", "intuition": "...", "code_example": "...", "common_pitfall": "...", "interview_test_question": "..." }"

---

### Claude's Response

```json
{
  "definition": "Big-O notation expresses how an algorithm's runtime or memory usage grows as the input size increases.",
  "intuition": "Imagine searching for a name in a phonebook. Checking every page is O(n). Opening to the middle and halving the search each time is O(log n). Going directly to the page is O(1).",
  "code_example": "# O(n)\nfor i in range(n):\n    print(i)\n\n# O(n²)\nfor i in range(n):\n    for j in range(n):\n        print(i, j)",
  "common_pitfall": "Students confuse Big-O with actual speed. O(n) is not always faster than O(n²) for small inputs — Big-O describes growth rate, not absolute performance.",
  "interview_test_question": "If I replace this nested loop with a HashMap lookup, what does the time complexity change from and to — and why?"
}
```

⚠️ **Flag:** Claude.ai wrapped this in backtick-json fences despite being told not to. The JSON content is valid — but a downstream parser would break on the fences. **Fix on Day 2: use `response_schema` + Pydantic validation.**

---

### Score: 5 / 5

**Why:**
- Every field is exactly what was specified — no hallucinated keys, no missing fields
- `common_pitfall` is the most valuable field: "growth rate, not absolute performance" is a nuance most explanations skip entirely
- `interview_test_question` gives the student an immediate practice prompt — best closing hook of all 6 patterns
- The phonebook analogy in `intuition` is the clearest single-sentence analogy across all 6 patterns
- Fence-wrapping is a tool limitation, not a content failure — content scores 5

**What made STRUCTURED OUTPUT work:**
- Schema-first thinking forced five distinct angles with zero overlap
- Output is machine-readable — can be piped into a flashcard app, Notion DB, or quiz tool
- Best pattern when the output will be consumed by code or must be consistent across many topics
- The fence-wrapping bug is the teaching moment: looks correct to a human, breaks a parser

---

## Pattern 5 — SYSTEM PROMPT

### The Setup

**System / Custom Instructions:**
> "You are a senior placement coach for B.Tech CSE students at an Indian engineering college. You prepare students for TCS / Infosys / Cognizant interviews. You explain technical concepts in 50-80 words max, conversationally, with one concrete code example."

**User prompt:**
> "Explain Big-O notation."

---

### Claude's Response

> Big-O tells you how your code behaves as data grows — not on 10 items, but on 10 lakh. O(n) means one loop; doubles input, doubles time. O(n²) is a nested loop; doubles input, quadruples time. In interviews, always state the complexity of your solution out loud.
> ```python
> for i in arr:       # O(n)
>     for j in arr:   # O(n²)
> ```

---

### Score: 5 / 5

**Why:**
- 62 words — hits the 50-80 word target precisely
- "10 lakh" is culturally calibrated without being re-instructed — the system prompt reproduced the contextual awareness of Pattern 1 in 3 words ("Indian engineering college")
- Inline code comments (`# O(n)`) are the most efficient annotation possible
- "Always state the complexity out loud" — same interview tip as Pattern 1, compressed to one sentence
- User prompt was 3 words. Output quality rivals Pattern 1. That ratio is the whole point.

**What made SYSTEM PROMPT work:**
- The word-count constraint ("50-80 words") forced prioritisation more effectively than any content instruction
- Separating stable role (system) from variable task (user) means the coach persona is written once and reused across 100+ topics
- Best pattern for building study bots, placement prep tools, or any app where the same persona answers varied questions
- Comparison to Pattern 1: same quality, 85% fewer words in the user prompt

---

## Pattern 6 — PROMPT CHAINING (3 Conversations)

### Conversation 1 — Extract

**Prompt:** "List the 5 most important sub-concepts a B.Tech student must understand about Big-O notation. Just the list, no explanation."

**Output:**
1. Definition of Big-O and what it measures
2. The five common complexities: O(1), O(log n), O(n), O(n log n), O(n²)
3. How to identify complexity by reading code structure
4. Time vs space complexity distinction
5. Why interviewers ask — what it signals about engineering thinking

---

### Conversation 2 — Expand

**Prompt:** "For each of these 5 sub-concepts of Big-O notation, write a 1-paragraph explanation tailored to a 3rd-year B.Tech CSE student preparing for placement interviews: [pasted list]"

**Output:**

> **1. Definition:** Big-O notation expresses how an algorithm's runtime or memory grows as input size grows. It strips away constants to focus on the growth pattern. Think of it as: "If the data doubles, what happens to my code?"
>
> **2. Five complexities:** O(1) is instant — HashMap lookups. O(log n) halves the problem — binary search. O(n) visits every element — a single for-loop. O(n log n) is sorting's gold standard — merge sort. O(n²) compares everything with everything — nested loops, avoid if possible.
>
> **3. Reading code:** One loop = O(n). Loop inside a loop = O(n²). Loop that halves a variable each step = O(log n). Recursive call that branches into two identical sub-calls = O(2ⁿ). These four rules classify 90% of interview code in under 10 seconds.
>
> **4. Time vs space:** Time counts operations. Space counts memory. A HashMap storing n items costs O(n) space. A recursive function going n levels deep costs O(n) stack space. Interviewers often ask for both — never answer time complexity without mentioning space.
>
> **5. Why interviewers ask:** Big-O signals you think about production scale, not just correctness. A function that works on 100 rows but times out on 10 million is a bug in disguise. TCS and Infosys want engineers who design for the worst case — Big-O is how you prove you do.

---

### Conversation 3 — Polish

**Prompt:** "Synthesise these 5 paragraphs into ONE concise 80-word interview-prep explanation of Big-O notation. Preserve all 5 sub-concepts. Conversational tone. End with one practice question. [pasted paragraphs]"

**Final Output:**

> Big-O describes how your code grows as data scales — not on 10 items, but on 10 lakh. O(1) is constant, O(log n) halves each step, O(n) visits everything once, O(n log n) is sorting's sweet spot, O(n²) is the nested-loop trap. One loop = O(n), loop inside a loop = O(n²). Always state both time and space complexity — it tells the interviewer you think beyond "does it work" to "does it survive real data."
>
> **Practice question:** What is the time and space complexity of bubble sort — and how would you improve it?

---

### Score: 5 / 5

**Why:**
- The final 80-word paragraph is the strongest single output across all 6 patterns — covers all 5 sub-concepts in one coherent, readable breath
- No single-prompt run produced all 5 sub-concepts in a tight paragraph — chaining is what made it possible
- The practice question closes with action, not just knowledge
- 3 calls, each with one job — the quality compounds across calls rather than averaging out

**What made PROMPT CHAINING work:**
- Each call had exactly one job: Extract → Expand → Polish — no call tried to do all three
- The list from Call 1 acted as a contract — Call 2 couldn't drift because it was anchored to 5 specific items
- Call 3 had rich, structured material to compress — it wasn't guessing, it was editing
- Best pattern for: study guides, structured explainers, any output where quality matters more than speed

---

## All Six Patterns — Head to Head

| Pattern | Length | Score | Best used for |
|---|---|---|---|
| 1 — PERSONA | Long | 5/5 | Deep 1-on-1 explanation |
| 2 — FEW-SHOT | Short | 4/5 | Flashcards, glossaries |
| 3 — CHAIN-OF-THOUGHT | Medium | 4/5 | Teaching the reasoning process |
| 4 — STRUCTURED OUTPUT | Structured (JSON) | 5/5 | Apps, tools, parseable output |
| 5 — SYSTEM PROMPT | Short | 5/5 | Reusable bots, study tools |
| 6 — PROMPT CHAINING | Long (3 calls) | 5/5 | High-quality study guides |

---

## Reflection — Which Patterns Will I Use With Students?

The patterns I will use most are **Pattern 5 (System Prompt)** and **Pattern 6 (Prompt Chaining)**, because:

**Pattern 5** lets me build a reusable placement-prep assistant that a student can use across 50+ DSA topics without rewriting the persona each time. The 50-80 word constraint forces the model to prioritise — students get dense, useful output, not textbook padding. Once the system prompt is written, the student's job is just to ask the question.

**Pattern 6** is for when quality really matters — topics like Dynamic Programming or System Design that need structured, comprehensive coverage. The Extract → Expand → Polish pipeline produces output that rivals a textbook section. It also teaches students a thinking framework they can apply manually in their own study notes.

**Pattern 1 (Persona)** is my third pick for live coaching demonstrations — it produces the most human, conversational output, which is what you want when showing students what a strong explanation actually sounds like in a 1-on-1 session.

---
