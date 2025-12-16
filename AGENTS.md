## 🤖 AGENTS.md: AI Assistant Instructions

This file provides **specific implementation instructions** for AI code assistants working on this **React Component Library** using **TypeScript**.

> **Note:** For required developer skills and learning resources, see [SKILLS.md](./SKILLS.md).

---

### 1. ⚙️ Available Commands

| Command                   | Purpose                                |
| :------------------------ | :------------------------------------- |
| `npm install`             | Install all dependencies               |
| `npm run storybook`       | Start Storybook dev server (port 6006) |
| `npm run build-storybook` | Build static Storybook                 |
| `npm run build`           | Build component library with Rollup    |
| `npx vitest`              | Run unit tests with Vitest             |
| `npm run lint`            | Lint source files with ESLint          |
| `npm run format`          | Format code with Prettier              |

---

### 2. 🏗️ Component Generation Workflow

When creating a new component, **ALWAYS** follow this exact sequence:

#### Step 1: Check for Design Tokens

**BEFORE** generating any component code:

1. Check if `src/app/styles/variables.css` exists
2. If **NOT present**, **IMMEDIATELY create it** with this starter template:

```css
:root {
  /* Colors */
  --color-primary: #0070f3;
  --color-secondary: #7928ca;
  --color-text: #333;
  --color-text-light: #666;
  --color-background: #fff;
  --color-border: #e1e1e1;

  /* Spacing Scale */
  --spacing-xs: 4px;
  --spacing-sm: 8px;
  --spacing-md: 16px;
  --spacing-lg: 24px;
  --spacing-xl: 32px;

  /* Typography */
  --font-size-sm: 14px;
  --font-size-md: 16px;
  --font-size-lg: 18px;
  --font-weight-normal: 400;
  --font-weight-medium: 500;
  --font-weight-bold: 700;
}
```

#### Step 2: Create Component Folder Structure

For a component named `Button` in the **atoms** category, create:

```
src/components/atoms/Button/
├── index.ts                  # Barrel export
├── Button.tsx                # Component implementation
├── Button.styles.scss        # BEM styles (NO CSS Modules)
├── Button.types.ts           # TypeScript interfaces
└── Button.test.tsx           # Vitest tests
```

**Folder Locations:**

- **Atoms:** `src/components/atoms/` (Buttons, Inputs, Icons)
- **Molecules:** `src/components/molecules/` (SearchBar, FormField)
- **Organisms:** `src/components/organisms/` (Header, Card, Modal)

#### Step 3: Implement the 5 Required Files

**1. `Button.types.ts`** - Define TypeScript interfaces first:

```tsx
export interface ButtonProps {
  children: React.ReactNode;
  variant?: 'primary' | 'secondary';
  disabled?: boolean;
  onClick?: () => void;
}
```

**2. `Button.tsx`** - Component implementation:

```tsx
import React from 'react';
import { ButtonProps } from './Button.types';
import './Button.styles.scss';

const Button: React.FC<ButtonProps> = ({
  children,
  variant = 'primary',
  disabled = false,
  onClick,
}) => {
  return (
    <button className={`button button--${variant}`} disabled={disabled} onClick={onClick}>
      {children}
    </button>
  );
};

export default Button;
```

**3. `Button.styles.scss`** - BEM styles with tokens:

```scss
.button {
  padding: var(--spacing-sm) var(--spacing-md);
  font-size: var(--font-size-md);
  border: none;
  cursor: pointer;

  &--primary {
    background-color: var(--color-primary);
    color: var(--color-background);
  }

  &--secondary {
    background-color: var(--color-secondary);
    color: var(--color-background);
  }

  &:disabled {
    opacity: 0.5;
    cursor: not-allowed;
  }
}
```

**4. `Button.test.tsx`** - Vitest tests (minimum 80% coverage):

```tsx
import { render, screen, fireEvent } from '@testing-library/react';
import { describe, it, expect, vi } from 'vitest';
import Button from './Button';

describe('Button', () => {
  it('renders children correctly', () => {
    render(<Button>Click me</Button>);
    expect(screen.getByText('Click me')).toBeInTheDocument();
  });

  it('calls onClick when clicked', () => {
    const handleClick = vi.fn();
    render(<Button onClick={handleClick}>Click me</Button>);
    fireEvent.click(screen.getByText('Click me'));
    expect(handleClick).toHaveBeenCalledTimes(1);
  });

  it('is disabled when disabled prop is true', () => {
    render(<Button disabled>Click me</Button>);
    expect(screen.getByText('Click me')).toBeDisabled();
  });
});
```

**5. `index.ts`** - Barrel export:

```ts
export { default } from './Button';
export type { ButtonProps } from './Button.types';
```

---

### 3. 🎨 Styling Rules

#### BEM Methodology (Mandatory)

**Block Element Modifier** naming convention:

- **Block:** `.button`
- **Element:** `.button__icon`
- **Modifier:** `.button--primary`

**SCSS Nesting:**

```scss
.card {
  // Block styles

  &__header {
    // Element styles

    &--active {
      // Modifier styles
    }
  }

  &--featured {
    // Block modifier
  }
}
```

#### Design Token Usage (Mandatory)

**❌ NEVER do this:**

```scss
.button {
  background-color: #0070f3; /* Hardcoded value */
  padding: 16px; /* Hardcoded value */
}
```

**✅ ALWAYS do this:**

```scss
.button {
  background-color: var(--color-primary);
  padding: var(--spacing-md);
}
```

#### Style Import Pattern

Import styles in the component file:

```tsx
import './Button.styles.scss'; // NOT: import styles from './Button.module.scss'
```

---

### 4. 📝 TypeScript Standards

#### Strict Typing Requirements

**❌ FORBIDDEN:**

```tsx
const Button = (props: any) => { ... }  // NO 'any' type
```

**✅ REQUIRED:**

```tsx
interface ButtonProps {
  children: React.ReactNode;
  onClick?: () => void;
}

const Button: React.FC<ButtonProps> = ({ children, onClick }) => { ... }
```

#### Type Organization

- **Simple types:** Can stay in component file
- **Complex types:** Move to `[Component].types.ts`
- **Shared types:** Consider creating `src/types/` folder

#### Export Pattern

**Component file (`Button.tsx`):**

```tsx
export default Button; // Default export
```

**Barrel file (`index.ts`):**

```ts
export { default } from './Button';
export type { ButtonProps } from './Button.types';
```

---

### 5. 🧪 Testing Requirements

#### Coverage Standards

- **Minimum:** 80% code coverage for all components
- **Test Location:** Colocated with component (`Button.test.tsx`)
- **Framework:** Vitest + React Testing Library + Playwright

#### What to Test

1. **Rendering:** Component renders correctly
2. **Props:** All props work as expected
3. **Interactions:** User interactions trigger correct behavior
4. **Accessibility:** Basic a11y checks (use Storybook addon for comprehensive testing)
5. **Edge Cases:** Disabled states, error states, empty states

#### Test File Template

```tsx
import { render, screen } from '@testing-library/react';
import { describe, it, expect } from 'vitest';
import ComponentName from './ComponentName';

describe('ComponentName', () => {
  it('should render correctly', () => {
    render(<ComponentName />);
    // Add assertions
  });

  // Add more tests...
});
```

---

### 6. 🚫 Restrictions & Mandates

#### Absolute Prohibitions

- ❌ **NO** class components (use functional components only)
- ❌ **NO** CSS Modules (`.module.scss`)
- ❌ **NO** `any` type in TypeScript
- ❌ **NO** hardcoded style values (use tokens)
- ❌ **NO** `dangerouslySetInnerHTML` (security risk)

#### Mandatory Requirements

- ✅ **MUST** create all 5 files for every component
- ✅ **MUST** use BEM methodology for CSS class names
- ✅ **MUST** reference design tokens for all style values
- ✅ **MUST** achieve 80% test coverage minimum
- ✅ **MUST** use TypeScript strict mode
- ✅ **MUST** check for `variables.css` before creating components

---

### 7. 📚 Storybook Integration

When creating components, also create a Storybook story:

**`Button.stories.tsx`:**

```tsx
import type { Meta, StoryObj } from '@storybook/react';
import Button from './Button';

const meta: Meta<typeof Button> = {
  title: 'Atoms/Button',
  component: Button,
  tags: ['autodocs'],
};

export default meta;
type Story = StoryObj<typeof Button>;

export const Primary: Story = {
  args: {
    children: 'Primary Button',
    variant: 'primary',
  },
};

export const Secondary: Story = {
  args: {
    children: 'Secondary Button',
    variant: 'secondary',
  },
};

export const Disabled: Story = {
  args: {
    children: 'Disabled Button',
    disabled: true,
  },
};
```

---

### 8. ✅ Pre-Submission Checklist

Before considering a component complete, verify:

- [ ] `src/app/styles/variables.css` exists
- [ ] All 5 required files created
- [ ] BEM methodology used in SCSS
- [ ] All styles use design tokens (no hardcoded values)
- [ ] TypeScript strict mode passes (no `any` types)
- [ ] Tests written and passing (80%+ coverage)
- [ ] Storybook story created
- [ ] Component exported via barrel file
- [ ] ESLint passes (`npm run lint`)
- [ ] Prettier formatting applied (`npm run format`)
