# Commit Genie

Commit Genie is an AI-powered developer tool that generates clear, conventional Git commit messages from a short description of code changes.

It provides a simple interface where developers can describe what they changed, select the appropriate commit type, and receive an AI-generated commit message.

## Live Demo

**Live App:** https://commit-genie.vercel.app

**GitHub Repository:** https://github.com/Fatimaanees132/Commit-genie.git

---

## Features

* Generate Git commit messages using Google Gemini
* Supports conventional commit types
* Simple and responsive interface
* Character count and input validation
* Loading and error states
* Accessible form controls
* Keyboard-friendly interaction
* Reduced-motion support
* Server-side API integration
* Responsive design for different screen sizes

---

## Tech Stack

* **Next.js**
* **React**
* **TypeScript**
* **Google Gemini API**
* **@google/genai**
* **Jest**
* **React Testing Library**
* **Vercel**

---

## AI Integration

Commit Genie uses **Google Gemini** to generate commit messages.

The Gemini API is called from a server-side API route rather than directly from the browser. This keeps the API key private and prevents exposing credentials to the client.

The application uses the environment variable:

```env
GEMINI_API_KEY=your_gemini_api_key
```

The Gemini model configured in the project is:

```text
gemini-3.7-flash
```

### Request Flow

```text
User
  ↓
Commit Genie UI
  ↓
Next.js API Route
  ↓
Google Gemini API
  ↓
Generated Commit Message
  ↓
User Interface
```

---

## Project Architecture

The application follows a simple Next.js structure.

```text
commit-genie/
├── src/
│   ├── app/
│   │   └── api/
│   │       └── generate-commit/
│   │           └── route.ts
│   ├── components/
│   │   └── ...
│   └── lib/
│       └── ...
├── public/
├── package.json
├── README.md
└── ...
```

### API Route

The `/api/generate-commit` route receives the user's commit information and communicates with Google Gemini on the server.

This keeps the Gemini API key out of the client-side code.

---

## Local Setup

### 1. Clone the repository

```bash
git clone https://github.com/Fatimaanees132/Commit-genie.git
cd Commit-genie
```

### 2. Install dependencies

```bash
npm install
```

### 3. Create environment variables

Create a `.env.local` file:

```env
GEMINI_API_KEY=your_gemini_api_key
```

Do not commit `.env.local` or your API key to GitHub.

### 4. Start the development server

```bash
npm run dev
```

Open:

```text
http://localhost:3000
```

### 5. Build the application

```bash
npm run build
```

The production build completed successfully during project verification.

---

## Testing

The project uses Jest and React Testing Library.

Command used:

```bash
npm test
```

### Test Results

```text
PS C:\Users\User\Downloads\commit-genie> npm test

> commit-genie@1.0.0 test
> jest

PASS src/lib/__tests__/commit.test.ts (7.62 s)
PASS src/components/__tests__/CommitForm.test.tsx (16.26 s)

Test Suites: 2 passed, 2 total
Tests:       7 passed, 7 total
Snapshots:   0 total
Time:        44.323 s
Ran all test suites.
```

**Result: 2/2 test suites passed, 7/7 tests passed.**

---

## Deployment

The application is
