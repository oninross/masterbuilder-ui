## ⚛️ AGENTS.md for React/Next.js (TypeScript)

This file provides specific instructions for AI code assistants working on this **React/Next.js** project using **TypeScript**.

### 1. ⚙️ Project Setup and Execution

| Command             | Description                                             |
| :------------------ | :------------------------------------------------------ |
| `npm install`       | Install all required dependencies.                      |
| `npm run dev`       | Start the Next.js development server.                   |
| `npm run build`     | Build the project for production.                       |
| `npm run start`     | Start the production server after a build.              |
| `npx vitest`        | Run unit tests using Vitest (Storybook plugin enabled). |
| `npm run storybook` | Start the Storybook development server.                 |

---

### 2. ✅ Testing

- **Primary Tool:** **Vitest** and **React Testing Library**.
- **Test Location:** Tests must be **colocated** with the component.
- **Requirement:** Every new component, hook, or API endpoint must have a corresponding test file ensuring at least **80% code coverage**.

---

### 3. 🎨 Code Style and Architecture

#### A. File & Folder Structure

- **Atomic Design Placement:**
  - **Atoms:** `src/app/components/atoms/` (Buttons, Inputs).
  - **Molecules:** `src/app/components/molecules/` (Search Bar).
  - **Organisms:** `src/app/components/organisms/` (Headers, Cards).
- **Mandatory Deliverables:** When generating a component, **ALWAYS** create the component folder containing these **5 files**:
  1. `index.ts` (Barrel file exporting default: `export { default } from './[Component]';`)
  2. `[Component].tsx` (Main component)
  3. `[Component].styles.scss` (Standard SCSS, NO Modules)
  4. `[Component].types.ts` (Interfaces/Types)
  5. `[Component].test.tsx` (Unit Tests)

#### B. Component Conventions

- **Exports Pattern:**
  - **Component File (`Button.tsx`):** Use `export default`.
    ```tsx
    const Button: React.FC<ButtonProps> = ({ children }) => { ... };
    export default Button;
    ```
  - **Barrel File (`index.ts`):** Re-export the default.
    ```ts
    export { default } from './Button';
    ```
- **Directives:** Default to Server Components. Add `'use client';` at the top only if hooks or browser APIs are needed.

#### C. Styling (BEM Methodology)

- **Methodology:** Use **BEM** (Block Element Modifier).
- **File Naming:** Use `[Component].styles.scss`.
- **🚫 RESTRICTION:** **DO NOT** use CSS Modules (`.module.scss`).
- **Global Tokens:** All color, spacing, and typography values **must** be defined as **CSS Variables (tokens)** in `src/app/styles/variables.css`.
  - **Creation Mandate:** **If `src/app/styles/variables.css` is not present, the AI must create it** with a basic set of design tokens (e.g., `--color-primary`, `--spacing-md`, etc.).
- **Implementation:**
  - Import styles globally in the component: `import "./Button.styles.scss";`
  - **SCSS Usage:** Always reference the tokens (e.g., `background-color: var(--color-primary);`).
  - **Markup Example:**
    ```tsx
    <div className="card">
      <div className="card__header card__header--active">Title</div>
    </div>
    ```
  - **SCSS Example:**
    ```scss
    .card {
      &__header {
        &--active { ... }
      }
    }
    ```

#### D. TypeScript

- **Strict Typing:** Explicitly define types for props/state. Move complex types to `[Component].types.ts`.
- **Avoid `any`:** Strict prohibition on `any`.

---

### 4. 🚫 Restrictions and Priorities

#### ⚠️ Mandatory Prerequisites: Global CSS Tokens

- **CSS Tokens Check:** BEFORE generating any component code, **ALWAYS** check for the existence of `src/app/styles/variables.css`.
- **Creation Mandate:** If `src/app/styles/variables.css` is **not present**, **IMMEDIATELY create it** with basic tokens.
- **Token Usage:** Component styles **must** reference tokens (`var(--token-name)`) for color, spacing, and typography; **never** hardcoded values.

> **Required `variables.css` Starter Example:**
>
> ```css
> :root {
>   /* Colors */
>   --color-primary: #0070f3;
>   --color-text: #333;
>   /* Spacing Scale */
>   --spacing-sm: 8px;
>   --spacing-md: 16px;
> }
> ```

---

- **Class Components:** Forbidden. Use **Functional Components** and **Hooks**.
- **Data Fetching:** Prefer Next.js Server Components (`async/await`) for data fetching. Use `SWR` or `React Query` for client-side updates.
- **Security:** Sanitize inputs; avoid `dangerouslySetInnerHTML`.
- **Import Aliases:** Always use absolute imports (e.g., `import { Button } from "@/components/atoms/Button";`).
