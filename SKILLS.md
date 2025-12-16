## 🛠️ SKILLS.md: Frontend Development UI Component Library

This document outlines the **required skills and competencies** for contributing to this React component library.

> **Note:** For AI-specific implementation instructions, see [AGENTS.md](./AGENTS.md).

---

### 1. 🚀 Core Web Fundamentals

#### HTML & CSS

- **HTML5:** Semantic markup, accessibility (ARIA), WCAG 2.1 AA compliance
- **CSS3:** Advanced Flexbox, CSS Grid, responsive design principles
- **SCSS/SASS:** Preprocessor features (variables, nesting, mixins, functions)
- **BEM Methodology:** Block Element Modifier naming conventions for scalable CSS
- **CSS Variables:** Custom properties for design tokens and theming systems

#### JavaScript & TypeScript

- **Modern JavaScript (ES6+):**
  - Promises, async/await, closures, event loop
  - Modules (import/export), destructuring, spread/rest operators
  - Array methods (map, filter, reduce, etc.)
- **TypeScript:**
  - Strong typing with interfaces, types, and generics
  - Strict mode configuration and best practices
  - Type inference and type guards
  - Utility types (Partial, Pick, Omit, etc.)

---

### 2. ⚛️ React Ecosystem

#### Core React Skills

- **Functional Components:** Modern React development patterns
- **React Hooks:**
  - State management: `useState`, `useReducer`
  - Side effects: `useEffect`, `useLayoutEffect`
  - Context: `useContext`
  - Performance: `useMemo`, `useCallback`, `React.memo`
  - Refs: `useRef`, `useImperativeHandle`
  - Custom hooks for reusable logic
- **Component Patterns:**
  - Atomic Design methodology (Atoms, Molecules, Organisms)
  - Composition over inheritance
  - Controlled vs uncontrolled components
  - Render props and higher-order components (when appropriate)

#### Component Library Development

- **Library Architecture:**
  - Building distributable React libraries
  - Peer dependencies management
  - CommonJS vs ESM module formats
  - Tree-shaking and bundle optimization
- **API Design:**
  - Creating intuitive, flexible component APIs
  - Props design and default values
  - Component composition patterns
  - Extensibility and customization strategies

---

### 3. 🧪 Testing & Quality

#### Testing Skills

- **Vitest:** Modern testing framework for Vite-based projects
- **React Testing Library:**
  - User-centric testing approach
  - Query methods (getBy, findBy, queryBy)
  - User event simulation
  - Async testing patterns
- **Playwright:** Browser automation for E2E and integration tests
- **Test Strategy:**
  - Unit testing components and hooks
  - Integration testing component interactions
  - Accessibility testing
  - Test coverage analysis (80% minimum)

#### Code Quality

- **ESLint:** Understanding and configuring linting rules
- **Prettier:** Code formatting standards
- **Git:** Version control workflows (branching, merging, rebasing, conflict resolution)
- **Code Review:** Giving and receiving constructive feedback

---

### 4. 📚 Storybook & Documentation

- **Storybook Fundamentals:**
  - Component-driven development workflow
  - Writing stories for component states and variants
  - Using addons (a11y, docs, interactions)
  - MDX documentation
- **Component Documentation:**
  - Writing clear prop descriptions
  - Usage examples and best practices
  - Accessibility guidelines
  - Migration guides

---

### 5. 🔧 Build Tools & Workflow

#### Development Tools

- **Rollup:** Module bundler for libraries (vs Webpack for applications)
- **Vite:** Fast development server and build tool
- **TypeScript Compiler:** Configuration and declaration file generation
- **Source Maps:** Debugging in development and production

#### Project Structure

- **Atomic Design Organization:**
  - Atoms: Basic building blocks (Button, Input, Icon)
  - Molecules: Simple combinations (SearchBar, FormField)
  - Organisms: Complex components (Header, Card, Modal)
- **File Organization:**
  - Component colocated files (component, styles, types, tests)
  - Barrel exports for clean imports
  - Shared utilities and types

---

### 6. ♿ Accessibility (A11y)

- **WCAG Standards:** Understanding WCAG 2.1 AA requirements
- **Keyboard Navigation:** Full keyboard accessibility for all interactive elements
- **Screen Readers:** ARIA attributes, roles, and states
- **Semantic HTML:** Using appropriate elements for their intended purpose
- **Focus Management:** Visible focus indicators and logical focus order
- **Color Contrast:** Meeting minimum contrast ratios
- **Testing Tools:** Using automated tools (Storybook a11y addon) and manual testing

---

### 7. 🎯 Design Systems & Theming

- **Design Tokens:** CSS custom properties for colors, spacing, typography
- **Token Architecture:** Organizing tokens by category and purpose
- **Theming:** Creating themeable components with CSS variables
- **Design-Developer Collaboration:** Working with design tools (Figma, Sketch)
- **Consistency:** Maintaining visual and behavioral consistency across components

---

### 8. 🔒 Security & Performance

#### Security

- **Input Validation:** Sanitizing user inputs
- **XSS Prevention:** Avoiding `dangerouslySetInnerHTML`
- **Dependency Management:** Keeping dependencies updated and secure

#### Performance

- **Bundle Size:** Minimizing component bundle sizes
- **Tree Shaking:** Ensuring components are tree-shakeable
- **Render Optimization:** Using memoization appropriately
- **Lazy Loading:** Code splitting for large components

---

### 9. � Professional Skills

- **Problem Solving:** Debugging complex issues with browser DevTools
- **Communication:** Clear technical writing and verbal communication
- **Collaboration:** Working effectively in teams and across disciplines
- **Agile Workflows:** Participating in sprints, standups, and retrospectives
- **Code Reviews:** Providing constructive feedback and learning from others
- **Continuous Learning:** Staying updated with React and web development trends

---

### 10. 📖 Learning Resources

#### Official Documentation

- [React Documentation](https://react.dev) - Official React docs
- [TypeScript Handbook](https://www.typescriptlang.org/docs/) - TypeScript guide
- [Vitest Documentation](https://vitest.dev) - Testing framework
- [Storybook Documentation](https://storybook.js.org) - Component development

#### Methodologies & Patterns

- [Atomic Design](https://atomicdesign.bradfrost.com/) - Brad Frost's methodology
- [BEM Methodology](https://getbem.com/) - CSS naming conventions
- [React TypeScript Cheatsheet](https://react-typescript-cheatsheet.netlify.app/) - TypeScript patterns

#### Accessibility

- [WCAG Guidelines](https://www.w3.org/WAI/WCAG21/quickref/) - Accessibility standards
- [A11y Project](https://www.a11yproject.com/) - Accessibility resources
- [WebAIM](https://webaim.org/) - Accessibility tools and guides

#### Testing

- [Testing Library](https://testing-library.com/) - Testing best practices
- [Playwright Docs](https://playwright.dev/) - Browser automation

---

### 11. 🎯 Quick Reference

#### Essential Commands

```bash
npm install              # Install dependencies
npm run storybook        # Start Storybook (port 6006)
npm run build            # Build library with Rollup
npx vitest               # Run tests
npm run lint             # Lint code
npm run format           # Format code
```

#### Key Project Standards

- ✅ Functional components only (no class components)
- ✅ TypeScript strict mode (no `any` types)
- ✅ BEM methodology for CSS (no CSS Modules)
- ✅ Design tokens for all style values (no hardcoded values)
- ✅ 80% minimum test coverage
- ✅ 5-file component structure (index, component, styles, types, tests)
- ✅ Colocated tests with components
- ✅ WCAG 2.1 AA accessibility compliance
