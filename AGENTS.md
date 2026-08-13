# Agents Guide for Codescape Core UI

This document describes the agents available for the `@codescape/core-ui` project and how to leverage them for development, testing, and automation tasks.

## Overview

Agents are specialized automation tools that can be invoked to perform specific tasks within the VS Code development environment. They assist with code exploration, refactoring, documentation, testing, and CI/CD workflows.

## Available Agents

### 1. Explore Agent

**Purpose:** Fast, read-only codebase exploration and Q&A

**When to use:**

- Understanding the project structure and codebase organization
- Finding specific components, utilities, or patterns
- Answering questions about how components work
- Locating where specific functionality is implemented
- Gathering context before making changes

**Example usage:**

```
How are the DataTable component props defined?
Where are the utility functions used?
What testing patterns are used in this project?
```

**Thoroughness levels:**

- **quick**: Surface-level search, useful for fast lookups
- **medium**: Balanced exploration, good for understanding patterns
- **thorough**: Deep analysis, comprehensive understanding of feature implementations

### 2. Build & Test Agents

**Purpose:** Automated building, testing, and validation

**Capabilities:**

- Run the development server (`npm run dev`)
- Execute test suite (`npm run test` or `npm run test:watch`)
- Build for production (`npm run build`)
- Run linting (`npm run lint` or `npm run lint:fix`)
- Validate code quality

**When to use:**

- Validating changes before committing
- Running tests to ensure components work correctly
- Building for production deployments
- Checking code quality and style compliance

## Task-Specific Workflows

### Component Development Workflow

1. **Explore existing patterns** using the Explore agent to understand:
   - Current component structure in `src/components/`
   - Existing utility functions in `src/utility/`
   - Testing patterns used in `.test.tsx` files

2. **Create new component** following established patterns

3. **Test the component** using build & test agents:
   - Write tests in `ComponentName.test.tsx`
   - Run `npm run test:watch` to validate

4. **Document the component** with inline comments and type annotations

5. **Lint and validate** using the linting agent to ensure code quality

### Refactoring Workflow

1. **Understand scope** - Use the Explore agent to identify:
   - All files affected by the refactoring
   - Current usage patterns
   - Dependencies and relationships

2. **Plan changes** - Document what needs to change and why

3. **Execute refactoring** - Make changes incrementally

4. **Validate** - Use test and build agents to ensure nothing breaks

5. **Review** - Use the Explore agent to verify the refactored code meets requirements

### Bug Fix Workflow

1. **Reproduce issue** - Understand the problem by:
   - Examining test files related to the bug
   - Using the Explore agent to find the faulty code
   - Running the development server to see the issue

2. **Locate root cause** - Use the Explore agent to:
   - Trace execution flow
   - Identify where the bug originates
   - Check related components

3. **Implement fix** - Make targeted changes

4. **Test thoroughly** - Run all relevant tests to ensure:
   - The bug is fixed
   - No regressions are introduced

5. **Document** - Add comments explaining the fix if it's complex

## Project Structure

Understanding the project layout helps agents provide better assistance:

```
src/
├── components/          # React UI components
│   ├── data-table/     # DataTable component and related schemas
│   └── index.ts        # Component exports
├── utility/             # Shared utility functions
│   ├── classnames.ts   # Class name utilities
│   ├── table-cell-utils.ts  # Table-specific utilities
│   └── index.ts        # Utility exports
├── index.ts            # Main entry point
└── setupTests.ts       # Test configuration
```

## Development Scripts

Agents can invoke these npm scripts for various tasks:

| Script                    | Purpose                                |
| ------------------------- | -------------------------------------- |
| `npm run dev`             | Start development server with Vite     |
| `npm run build`           | Compile TypeScript and build with Vite |
| `npm run lint`            | Check code quality with ESLint         |
| `npm run lint:fix`        | Automatically fix linting issues       |
| `npm run test`            | Run tests once with Vitest             |
| `npm run test:watch`      | Run tests in watch mode                |
| `npm run preview`         | Preview production build               |
| `npm run publish:private` | Publish to private npm registry        |

## Technology Stack

Agents should be aware of the following technologies used in this project:

- **Language**: TypeScript 5.9+
- **Frontend Framework**: React 19.2+
- **Build Tool**: Vite 7+
- **Testing**: Vitest 4.0+
- **Testing Library**: @testing-library/react
- **Styling**: TailwindCSS (via classnames and tailwind-merge)
- **Linting**: ESLint with TypeScript support
- **Code Formatting**: Prettier

## Component Development Guidelines

When developing components, agents should ensure:

1. **Type Safety**
   - All props should have TypeScript interfaces
   - Export types from component files
   - Use strict type checking

2. **Testing**
   - Create `.test.tsx` file for each component
   - Test user interactions, not implementation
   - Use @testing-library/react patterns
   - Aim for high coverage of component logic

3. **Documentation**
   - Include JSDoc comments for components
   - Document complex logic with inline comments
   - Ensure props are documented in the interface

4. **Code Quality**
   - Follow ESLint rules (check `.eslintrc.json`)
   - Use Prettier for consistent formatting
   - Keep components focused and single-purpose

5. **Styling**
   - Use TailwindCSS classes where applicable
   - Use `clsx` for conditional class names
   - Use `tailwind-merge` to resolve class conflicts

## Common Agent Patterns

### Pattern 1: Understanding a Component

```
Agent Task: Explore the DataTable component structure
1. Find the DataTable component file
2. Identify the main component logic
3. Review the ColumnSchema type definition
4. Locate related utility functions
5. Check the test file for usage examples
```

### Pattern 2: Implementing a Feature

```
Agent Task: Add a new utility function
1. Explore existing utility patterns
2. Understand how utilities are structured
3. Create the new utility with TypeScript types
4. Add tests for the utility
5. Export from utility/index.ts
6. Run tests to verify
```

### Pattern 3: Fixing a Bug

```
Agent Task: Fix component behavior
1. Explore test files to understand expected behavior
2. Run the failing test
3. Trace the bug in component logic
4. Implement the fix
5. Re-run tests to confirm fix
6. Run full test suite to check for regressions
```

## Best Practices for Agent Usage

1. **Be Specific**: Provide clear, detailed instructions when invoking agents
2. **Understand Context**: Use the Explore agent first to understand the codebase before making changes
3. **Validate Changes**: Always run tests and linting before committing
4. **Document Decisions**: Leave clear comments explaining complex logic
5. **Incremental Changes**: Make small, focused changes rather than large refactors
6. **Review Results**: After agent operations, review the changes to ensure they meet requirements

## Troubleshooting

### Common Issues

**Issue:** Tests fail after making changes

- **Solution**: Use the Explore agent to understand test patterns, then review the changed code for logic errors

**Issue:** Linting errors after code changes

- **Solution**: Run `npm run lint:fix` to automatically fix formatting issues, or review the linting configuration

**Issue:** Build failures

- **Solution**: Check TypeScript errors first with `npm run build`, then review type definitions and imports

## Contributing with Agents

When contributing to this project:

1. **Start with exploration** to understand existing patterns
2. **Follow established conventions** discovered during exploration
3. **Write comprehensive tests** for any new functionality
4. **Ensure code quality** by running lint and build checks
5. **Document your changes** clearly in code and commit messages

## Resources

- [React Documentation](https://react.dev)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [Vite Documentation](https://vitejs.dev)
- [Vitest Documentation](https://vitest.dev)
- [Testing Library Best Practices](https://testing-library.com/docs/queries/about)
- [ESLint Configuration](https://eslint.org/docs/latest/use/configure/)
- [Prettier Configuration](https://prettier.io/docs/en/configuration.html)

## Questions or Issues?

If you encounter issues with agents or need clarification on development patterns:

1. Use the Explore agent to search for related code and patterns
2. Review existing test files for usage examples
3. Check the project configuration files (tsconfig.json, vite.config.ts)
4. Consult the project's GitHub issues or documentation
