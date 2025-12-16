# Take-home assignment: AI-assisted Language Practice

## Goal
Build a small web application that helps a user practice **English irregular verbs**.

The system should:
- Generate short exercises about irregular verbs
- Accept user answers
- Evaluate and correct answers
- Track basic user progress

You are free to **reduce scope** and make pragmatic tradeoffs. We value **clarity of design and correctness** over feature completeness.

---

## Functional requirements

### Practice flow
1. The user selects:
   - Topic: **English irregular verbs**
   - Difficulty (1–3)
   - Exercise type
2. The system generates an exercise.
3. The user submits an answer.
4. The system responds with:
   - Correct / incorrect
   - Correct form of the verb
   - Short explanation
5. The system records the attempt and updates progress.

---

## Exercise types
Implement **at least one**, more if you choose:
- Fill in the blank  
  *“Yesterday, I ___ (go) to the store.”*
- Rewrite sentence using correct tense  
- Multiple choice  
- Short free-text answer

---

## Progress tracking
Track at minimum:
- Number of attempts
- Number of correct answers
- Success rate (overall and per difficulty)

---

## AI integration
Use an LLM to:
1. Generate exercises about English irregular verbs
2. Evaluate and correct user answers

### Requirements
- AI responses **must be structured JSON**
- Responses must be validated before use
- The system must support:
  - **Stub mode** (deterministic, no network)
  - **Real mode** (calls an actual LLM if API key is present)

The application must run fully in stub mode.

---

## Backend requirements

### API endpoints (suggested)
You may change these if you prefer.

- `POST /api/session`
  - Input:
    ```json
    {
      "difficulty": 1,
      "exercise_type": "fill_blank"
    }
    ```
  - Output: `Exercise`

- `POST /api/attempt`
  - Input:
    ```json
    {
      "exercise_id": "uuid",
      "user_answer": "went"
    }
    ```
  - Output: `EvaluationResult`

- `GET /api/progress`
  - Output: progress summary

---

## Persistence
Use a database (SQLite, Postgres, etc.).

Store at minimum:
- Exercise prompt
- User answer
- Correct / incorrect
- Corrected answer
- Difficulty
- Timestamp

---

## Frontend requirements

- Single Page Application (SPA)
- Any modern framework (React, Vue, Svelte, etc.)
- Minimal UI is sufficient

### Required screens
- Practice screen (generate exercise, submit answer, see result)
- Progress view (success rate, recent attempts)

---

## Data contracts (example)

### Exercise
```json
{
  "id": "uuid",
  "exercise_type": "fill_blank",
  "difficulty": 2,
  "prompt": "Yesterday, I ___ (go) to the store."
}
```

### EvaluationResult

The evaluation result returned after submitting an answer should include:

- Whether the answer is correct
- The corrected form of the verb
- A short explanation

---

## Testing

Include automated tests for:

- Progress calculation logic
- One end-to-end API flow using AI stub mode

---

## Running the project locally

The repository must include clear instructions for:

- Installing dependencies
- Running backend and frontend locally
- Running the project in **AI stub mode**
- Running tests

A single command (or a small set of commands) to start the project is preferred.

---

## Scope and tradeoffs

This assignment is intentionally open-ended.  
You are encouraged to **reduce scope where appropriate** and explain your decisions in the README.

Examples:

- Fewer exercise types
- Simplified progress metrics
- Single user assumption
- Minimal styling

---

## Success criteria

We will focus on:

- API and data model design
- AI integration and validation
- Code clarity and structure
- Correctness and test coverage
- Thoughtful scoping and documentation
