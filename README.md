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

The application is deployed using Vercel.

### Production URL

https://commit-genie.vercel.app

### Vercel Environment Variable

The following environment variable is configured for the deployed application:

```text
GEMINI_API_KEY
```

The API key is stored as a Vercel environment variable rather than being exposed in the source code.

---

## Deployment Verification

The deployed application was tested with a real request.

### Verification

* Production application loads successfully.
* User can submit a commit description.
* Request reaches the server-side API route.
* Gemini generates a commit message.
* Generated result is displayed in the application.

---

## Error Handling

The application includes an error state for failed AI requests.

If the Gemini API request fails or the API key is missing/invalid, the application displays a readable error message instead of crashing.

This provides a better user experience when an external API is unavailable.

---

## Accessibility

Accessibility was tested using **axe DevTools** against the deployed application.

### Accessibility Audit

```text
Total Issues: 0
Critical:     0
Serious:      0
Moderate:     0
Minor:        0
Standard:     WCAG 2.1 AA
```

### Accessibility Features

The application includes several accessibility-focused implementations:

* Visible keyboard focus rings using `:focus-visible`
* Proper `<label>` associated with the textarea
* `aria-live` regions for status updates
* Accessible character-count feedback
* `role="alert"` for error messages
* `aria-invalid` for invalid form states
* `aria-describedby` for additional form information
* `prefers-reduced-motion` support

The final axe audit reported **0 accessibility issues**.

---

## Lighthouse Results

Lighthouse was run against the deployed application.

| Category       |   Score |
| -------------- | ------: |
| Performance    |  **84** |
| Accessibility  | **100** |
| Best Practices | **100** |
| SEO            | **100** |

### Summary

The application achieved perfect scores in Accessibility, Best Practices, and SEO. Performance scored **84**, leaving some room for future optimization.

---

## Known Limitations

* AI-generated commit messages may occasionally require manual adjustment.
* The quality of generated messages depends on the clarity of the user's description.
* The application currently focuses on generating commit messages rather than automatically analyzing a Git diff.
* Gemini API availability and response limits depend on the configured Google AI service.

---

## Deployment Checklist

* [x] Project runs locally
* [x] `npm install` completed successfully
* [x] `npm run build` completed successfully
* [x] Tests pass
* [x] GitHub repository created and pushed
* [x] Application deployed to Vercel
* [x] `GEMINI_API_KEY` configured in Vercel
* [x] Production app tested with a real request
* [x] Commit message successfully generated
* [x] Lighthouse audit completed
* [x] Accessibility audit completed
* [x] Error state tested
* [x] README completed

### Lighthouse

* Performance: **84**
* Accessibility: **100**
* Best Practices: **100**
* SEO: **100**

### Accessibility

* axe DevTools: **0 issues**
* WCAG 2.1 AA audit completed

### Testing

* Test suites: **2 passed**
* Tests: **7 passed**

---

## Reflection

### What was the hardest part?

The most challenging part was integrating the AI functionality while keeping the API key secure and making sure the frontend, server-side API route, and Gemini service communicated correctly. Handling loading and error states was also important because an AI request can fail for reasons outside the application's control.

### What would I do differently?

If I were rebuilding the project, I would spend more time improving the UI and adding more advanced commit-generation options. I would also consider adding Git diff support so the application could analyze actual code changes instead of relying only on a user's written description.

### What surprised me?

One thing that surprised me was how much work is involved beyond simply connecting an AI API. Testing, accessibility, error handling, deployment configuration, and performance all have a major impact on the quality of a real application.

---

## Final Submission

### Project

**Commit Genie — AI-powered Git commit message generator**

### Live Application

https://commit-genie.vercel.app

### GitHub Repository

https://github.com/Fatimaanees132/Commit-genie.git

### Evidence

* Test results: **2 test suites passed, 7 tests passed**
* Lighthouse: **84 / 100 / 100 / 100**
* Accessibility: **0 axe issues**
* Gemini API integration completed
* Production deployment verified

---

**Completed:** September 4, 2026
