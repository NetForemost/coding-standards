# 📘 Pull Request Guidelines  
## React + TypeScript + .NET Projects

These guidelines exist to keep the codebase clean, predictable, and maintainable.

They also help speed up PR reviews and reduce unnecessary back-and-forth.

> [!NOTE] 
> If your PR does not follow these rules, it will be requested for changes.

## 🎯 Core Philosophy

Before opening a PR, always ask yourself:

- Does this change only what my task requires?
- Did I follow existing patterns?
- Did I understand the code I wrote?
- Would another developer understand this PR in 6 months?

If the answer is no, fix it before opening the PR.

## ✅ PR Scope Rules (VERY IMPORTANT)

### A PR must:

- Contain only changes related to the assigned feature or fix
- Follow existing architecture and patterns
- Be minimal and focused

### A PR must NOT:

- Include unrelated refactors
- Modify random files because formatting changed
- Add or remove imports that are not required
- Add whitespace-only changes
- Reformat files unless explicitly requested
- Introduce files in new folders without approval

If you think something else needs fixing:

- Open another ticket
- Ask first

## 🧠 Think Before You Code (Especially With AI)

Using ChatGPT / Copilot / Gemini / Other is allowed.

Blind copy-paste is NOT.

You are expected to:

- Understand what every line does
- Be able to explain your code
- Validate types and logic
- Adapt output to project patterns

If you submit AI-generated code without reviewing it, your PR will be rejected.

## 📐 Follow Existing Design Patterns

Do not invent new patterns.

Example:

If the project uses:

```ts
interface User {
  id: string;
}
```

Do NOT introduce:

```ts
type User = {
  id: string;
}
```

Consistency is more important than personal preference.

This applies to:

- Folder structure
- Naming
- Services
- Hooks
- Controllers
- DTOs
- Domain models

Always mirror existing implementations.

## 🟦 TypeScript + React Standards
### 🚫 Avoid any

`any` removes type safety.

Bad:

```ts
const data: any = response.data;
```

Better:

```ts
interface ApiResponse {
  id: string;
  name: string;
}

const data: ApiResponse = response.data;
```

If unsure:

```rs
type ApiResponse = {
  id: string;
} | null;
```

Union types are preferred over `any`.

## ✅ Always Prefer Explicit Types

Props:

```ts
interface Props {
  title: string;
}
```

or (depending on the current project patten)

```ts
type Props {
    title: string;
}
```

State:

```ts
const [count, setCount] = useState<number>(0);
```

Callbacks:

```ts
const handleClick = (id: string): void => {}
```

### 🚫 No Unused Imports

Remove unused imports immediately.

If your PR contains unused imports, it will be rejected.

### 🚫 No Console Logs

Remove all console logs before committing.

### 🚫 No Commented Code

Bad:

```
// old logic
// const x = ...
```

Delete it.

Git already keeps history.

> [!NOTE] 
> Good comments are **context comments**. E.g. trying to explain why something was done in a specific way. Comments should not explain the code but provide business logic context if necessary.

Good:

```
// The business requires us to save browser data for audit purposes, that's why wo do this
```

## 🟥 Backend (.NET) Standards
### Follow Existing Architecture

Do NOT:
- Create random services
- Skip layers
- Bypass DTOs
- Return EF entities directly

Respect:
- Controllers
- Services
- Repositories
- Domain models

### No Magic Values 

> [!INFO] 
> (This applies to both front, back and any other app layer)

Bad:

```c#
if(status == 3)
```

Good:

```c#
if(status == OrderStatus.Completed)
```

### Use Strong Types

Avoid:
```c#
object result
```

Prefer:
```c#
OrderDto result
```

## 📁 File Placement Rules

Do not create files in new folders unless explicitly approved.

Always mirror existing structure.

If unsure, ask first.

## 🧪 Testing

Every PR must clearly state:
- What was tested
- How it was tested

Example:

```md
Tested:
- Created order manually
- Verified UI render
- Validated API response
```

### 📝 PR Description Template

Use this format:

#### What
Short description of change.

---

#### Why
Business or technical reason.

---

#### How
High-level approach.

---

#### Tested
Steps performed.

---
#### Notes (optional)
Anything reviewers should know.

### 🚨 Automatic Rejection Reasons

PR will be rejected if it contains:
- any
- unrelated changes
- commented code
- unused imports
- random formatting
- new folders without approval
- AI copy-paste without understanding
- missing PR description
- missing testing info

No exceptions.

### 🧭 Final Rule

If something is unclear:

ASK.

Guessing costs more time than asking.

### ✅ Goal

- Clean PRs
- Predictable architecture
- Fast reviews
- Strong engineers