# cursor-rules-golang

## Overview

**cursor-rules-golang** is a collection of best-practice Cursor rules and guidelines for Go projects. These rules help Go developers—both new and experienced—write clean, idiomatic, secure, and maintainable code, with a focus on API development using Go's standard library (`net/http`, `ServeMux`), error handling, testing, logging, and more.

Cursor rules are extra documentation and instructions that help AI assistants (like Cursor) and your team understand, navigate, and maintain your codebase more effectively.

---

## Why Use Cursor Rules?
- **Consistency:** Enforce Go best practices and project standards automatically.
- **Productivity:** Get in-editor guidance, code navigation, and quick fixes.
- **Onboarding:** Help new team members ramp up quickly with clear, actionable rules.
- **Quality:** Reduce bugs, improve security, and ensure maintainability.

---

## Getting Started

### 1. Prerequisites
- Go 1.22 or newer installed
- [Cursor](https://www.cursor.so/) editor or compatible AI assistant

### 2. Project Structure
Place all Cursor rules in the `.cursorrules/` directory at the root of your Go project:

```
PROJECT_ROOT/
├── .cursorrules/
│   ├── api-guidelines.mdc
│   ├── error-handling.mdc
│   ├── logging.mdc
│   ├── testing.mdc
│   └── ...
├── cmd/
├── internal/
├── pkg/
├── go.mod
└── ...
```

### 3. How to Use Cursor Rules

- **Automatic Guidance:** When you open your project in Cursor, the rules in `.cursorrules/` are automatically used to provide context-aware suggestions, code navigation, and best practices.
- **Rule Reference:** You can reference files in your rules using `[filename.go](mdc:filename.go)` to help the AI and your team find important code.
- **Customization:** Add or edit `.mdc` files in `.cursorrules/` to tailor rules to your team's needs. Use kebab-case for filenames and keep them descriptive.
- **No Code Changes Needed:** Cursor rules are documentation—they do not change your Go code, but help you and the AI write better code.

### 4. Example Rule (api-guidelines.mdc)

```markdown
---
description: Guidelines for developing APIs using Go's net/http package
globs: "**/*.go"
alwaysApply: true
---
# Go API Development Guidelines

- Use `net/http` and `ServeMux` for routing
- Implement proper error handling and input validation
- Use middleware for logging, authentication, etc.
- Write table-driven tests for handlers

```

### 5. Best Practices
- Keep rules focused (one topic per file)
- Update rules as your project evolves
- Encourage your team to read and follow the rules
- Use rules for onboarding new developers

---

## For Newcomers & Freshers
- **Read the rules in `.cursorrules/` before starting development.**
- **Follow the examples and code snippets in each rule.**
- **Ask questions in your team if a rule is unclear.**
- **Use Cursor's suggestions and quick fixes—they are powered by these rules!**

## For Experienced Go Developers
- **Customize rules to match your team's standards.**
- **Contribute new rules for advanced topics (e.g., performance, security, microservices).**
- **Use rules to enforce consistency and mentor junior developers.**

---

## Contributing
- Add new `.mdc` files to `.cursorrules/` for new guidelines
- Update existing rules as best practices evolve
- Review rules regularly as a team

---

## Resources
- [Go Documentation](https://golang.org/doc/)
- [Cursor Documentation](https://www.cursor.so/docs)
- [Effective Go](https://golang.org/doc/effective_go.html)
- [Go Code Review Comments](https://github.com/golang/go/wiki/CodeReviewComments)

---

## License
MIT