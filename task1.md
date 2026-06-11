# AI Day-1

## task 1

| Tool           | Likely approach                                                          | Quality signal                                  | Failure mode                                                  |
| -------------- | ------------------------------------------------------------------------ | ----------------------------------------------- | ------------------------------------------------------------- |
| **ChatGPT**    | Keyword overlap + cosine similarity (TF-IDF) using `collections.Counter` | Clean, readable, idiomatic code                 | May skip docstrings or quietly use non-standard libraries     |
| **Claude**     | More elaborate; may suggest multiple scoring approaches                  | Thorough explanation, strong edge-case handling | Can be over-engineered for the prompt                         |
| **Gemini**     | Often suggests `sklearn`-based similarity implementations                | Concise and direct                              | Most likely to violate the "standard library only" constraint |
| **Perplexity** | Basic implementation with references/explanations                        | Often cites sources and rationale               | May provide shorter or less complete code                     |


### Scoring guide for Task 1

| Score          | Correctness                                         | Readability                                      | Constraint Adherence                                                     |
| -------------- | --------------------------------------------------- | ------------------------------------------------ | ------------------------------------------------------------------------ |
| **5**          | Function works on test input and handles edge cases | Clean naming, docstring present, useful comments | Standard library only; returns specified dictionary shape                |
| **3 (anchor)** | Works on simple input but breaks on some edge cases | Generally readable but inconsistent              | One minor constraint violation                                           |
| **1**          | Does not run or returns incorrect output shape      | Cryptic code, no docstring                       | Uses prohibited libraries (`sklearn`, `spaCy`, etc.) despite constraints |


## Task-2

| Tool           | Likely approach                                                           | Quality signal                                                          | Failure mode                                                           |
| -------------- | ------------------------------------------------------------------------- | ----------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| **ChatGPT**    | Keyword overlap + cosine similarity using `Counter` and token frequencies | Best balance of simplicity and matching quality; clear reasoning output | Treats many JD words as "skills", causing noisy `missing_skills` lists |
| **Claude**     | Keyword extraction with stop-word filtering and match-percentage scoring  | Clean implementation, good documentation, strong constraint adherence   | Uses exact keyword matching only; limited semantic understanding       |
| **Gemini**     | Keyword extraction with stop-word filtering and JD coverage scoring       | Most concise and readable; good handling of empty JD edge case          | Simple overlap metric can under-score strong resumes with synonyms     |
| **Perplexity** | Hybrid approach: keyword matching, phrase extraction, weighted scoring    | Most ambitious logic; attempts skill detection and phrase analysis      | Over-engineered, heuristic-heavy, may produce inconsistent scores      |


Scoring Guide for Task 2
| Score          | Correctness                                                               | Readability                                      | Constraint Adherence                                           |
| -------------- | ------------------------------------------------------------------------- | ------------------------------------------------ | -------------------------------------------------------------- |
| **5**          | Function runs correctly, returns required dict, handles common edge cases | Clear naming, docstring, comments, usage example | Uses only Python standard library and follows prompt exactly   |
| **3 (anchor)** | Works on typical inputs but has scoring or extraction weaknesses          | Generally readable with minor inconsistencies    | Minor prompt deviation but no external dependencies            |
| **1**          | Incorrect output shape, runtime issues, or unreliable scoring             | Poor documentation or unclear logic              | Uses prohibited libraries/APIs or ignores required constraints |


## Task-3

| Tool           | Likely approach                                          | Quality signal                                               | Failure mode                                                 |
| -------------- | -------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **ChatGPT**    | Explicit step-by-step arithmetic with final verification | Clear reasoning chain, computes intermediate times correctly | Can be slightly verbose for simple problems                  |
| **Claude**     | Concise logical breakdown following the provided facts   | Efficient reasoning, preserves all steps                     | Sometimes overly brief if detailed reasoning is requested    |
| **Gemini**     | Validates the worked solution and restates calculations  | Direct and easy to follow                                    | May spend effort confirming instead of independently solving |
| **Perplexity** | Structured calculation with conclusion and comparison    | Clear final answer and arithmetic checks                     | Can be more formulaic and less explanatory                   |


Scoring Guide for Task 3

| Score          | Correctness                                         | Reasoning Quality                                      | Instruction Following                                          |
| -------------- | --------------------------------------------------- | ------------------------------------------------------ | -------------------------------------------------------------- |
| **5**          | All calculations correct; final answer correct      | Clear step-by-step reasoning with intermediate results | Shows reasoning as requested and answers the question directly |
| **3 (anchor)** | Correct answer but minor reasoning gaps             | Some steps omitted or compressed                       | Mostly follows instructions                                    |
| **1**          | Arithmetic or logic error leads to wrong conclusion | Missing or confusing reasoning                         | Ignores request for step-by-step explanation                   |



After all 3 tasks, each mentor's matrix looks like this:

| Tool           | Task 1 (Summarise) | Task 2 (Code) | Task 3 (Reason) | My Verdict                                                                                               |
| -------------- | ------------------ | ------------- | --------------- | -------------------------------------------------------------------------------------------------------- |
| **ChatGPT**    | 5                  | 5             | 5               | **Best all-rounder. Strong summarization, coding, and reasoning with consistent instruction following.** |
| **Claude**     | 5                  | 4             | 5               | **Best for detailed writing and careful reasoning. Produces thorough, well-documented solutions.**       |
| **Gemini**     | 4                  | 4             | 4               | **Good balance of speed and accuracy. Concise outputs but sometimes less comprehensive.**                |
| **Perplexity** | 4                  | 3             | 5               | **Strong when explanations and source-oriented thinking matter. More variable in coding tasks.**         |
