# Product Requirements Document (PRD): Cursor Rules for Go

## Project Title
**cursor-rules-golang**

## Version
1.0.0

## Date
May 23, 2025

## Author
[Your Name or Team Name]

## 1. Introduction

### 1.1 Purpose
The `cursor-rules-golang` project develops a tool to generate cursor rules for Go-based applications, focusing on API development using the standard library's `net/http` package and the `ServeMux` introduced in Go 1.22. These rules enforce coding standards, linting, formatting, navigation aids, and API-specific guidelines to improve code quality, consistency, and developer productivity.

### 1.2 Scope
The tool will:
- Generate customizable cursor rules based on Go best practices for API development.
- Integrate with development environments like VS Code, IntelliJ, and GoLand.
- Support static code analysis, formatting, navigation, and API-specific guidelines.
- Fetch rules from external sources (e.g., GitHub repositories) and organize them in a `.cursorrules/` directory.
- Be extensible for community contributions and custom rule definitions.

### 1.3 Target Audience
- Go developers building APIs with the standard library.
- Teams maintaining large Go codebases.
- Open-source contributors seeking consistent coding standards.

### 1.4 Expertise
This tool is developed with the assistance of an expert AI programming assistant specializing in Go API development. The assistant uses:
- The latest stable Go version (1.22 or newer).
- The standard library's `net/http` package and `ServeMux` for routing.
- RESTful API design principles, Go idioms, and best practices.
- Comprehensive backend development expertise across databases, scalability, security, and more.

## 2. Goals and Objectives

- **Primary Goal**: Automate cursor rule generation to enforce coding standards and best practices in Go API development.
- **Objectives**:
  - Enhance code readability, maintainability, and consistency.
  - Reduce manual configuration time for linting, formatting, and development tools.
  - Integrate with tools like `golangci-lint`, `go fmt`, and `go vet`.
  - Provide a user-friendly interface for rule customization.

## 3. Features and Functionality

### 3.1 Core Features
1. **Rule Generation**:
   - Generate rules based on Go best practices (e.g., Effective Go, Go Code Review Comments).
   - Support custom rule definitions via YAML/JSON configuration files.
   - Include API-specific rules for request handling, error management, and middleware.
   - Provide schema validation for rule files with descriptive error messages.
   - Include a `cursor-rules init` CLI wizard for first-time setup.

2. **Linting and Formatting**:
   - Integrate with `golangci-lint` for coding standards enforcement.
   - Configure advanced static analysis tools (`staticcheck`, `errcheck`).
   - Extend `go fmt` with API-specific style checks.
   - Provide real-time IDE feedback via robust LSP integration.
   - Offer quick fixes and code actions for common rule violations.

3. **API-Specific Guidelines**:
   - Enforce RESTful API design principles.
   - Guide usage of `net/http` and `ServeMux` for routing.
   - Recommend error handling, logging, and middleware best practices.
   - Auto-generate test scaffolds for new API endpoints.
   - Integrate code coverage tracking with `go test --cover`.

4. **Navigation and Productivity Aids**:
   - Generate rules for navigating API endpoints, handlers, and related files.
   - Offer context-aware suggestions for API tasks.
   - Provide LSP-based code completion and documentation.
   - Include a `cursor-rules feedback` command for user input.
   - Link to GitHub issues for community feedback.

5. **Extensibility**:
   - Enable custom rule definitions via a plugin system.
   - Support community-contributed rule sets.
   - Validate custom rules against JSON/YAML schemas.
   - Provide clear error messages for rule misconfigurations.
   - Include example rule templates and documentation.

### 3.2 Non-Functional Requirements
- **Performance**: Rule generation completes within 2 seconds for a 10,000-line codebase.
- **Compatibility**: Supports Go 1.22 and above.
- **Portability**: Runs on Windows, macOS, and Linux.
- **Scalability**: Handles codebases up to 1 million lines.

## 4. Technical Requirements

### 4.1 Technology Stack
- **Language**: Go
- **Dependencies**:
  - `golangci-lint` with extended configurations:
    - `staticcheck` for deep code analysis
    - `errcheck` for unchecked error detection
    - Race condition detection via `go test -race`
  - `go/parser` and `go/ast` for code analysis
  - YAML/JSON parsing libraries with schema validation
- **Build Tools**: `go build`, `go mod`
- **Testing**: 
  - `go test` with coverage tracking
  - Test scaffold generation
  - Integration test helpers

### 4.2 System Architecture
- **Input**: Go source files, configuration files (YAML/JSON), external rule sources (e.g., GitHub).
- **Processing**:
  - Parse Go code with `go/parser`.
  - Analyze API patterns and structures.
  - Generate rules from templates and configurations.
- **Output**: Cursor rule files, linting configs, IDE settings.

### 4.3 Integration Points
- **IDEs**: VS Code (via LSP), IntelliJ, GoLand.
- **CI/CD**: GitHub Actions, GitLab CI.
- **Tools**: `go fmt`, `golangci-lint`, `go vet`.

## 5. API Development Guidelines

The tool enforces the following guidelines for Go API development:

- **Core Principles**:
  - Use `net/http` and `ServeMux` (Go 1.22+) for API development.
  - Leverage Go's standard library for efficient, idiomatic APIs.
  - Follow RESTful API design principles and Go best practices.
  - Use Go 1.22 or newer.

- **Error Handling and Responses**:
  - Implement proper error handling with custom error types when beneficial.
  - Use appropriate HTTP status codes and correctly format JSON responses.

- **Security and Validation**:
  - Implement input validation for all endpoints.
  - Prioritize security, scalability, and maintainability.
  - Use prepared statements for database interactions to prevent SQL injection.

- **Performance**:
  - Utilize Go's concurrency features (e.g., goroutines) when beneficial.

- **Logging and Middleware**:
  - Implement logging with the standard `log` package or a simple custom logger.
  - Use middleware for cross-cutting concerns (e.g., logging, authentication).

- **Additional Features**:
  - Implement rate limiting and authentication/authorization using standard library features or simple custom implementations.
  - Include all necessary imports, package declarations, and setup code.
  - Leave no todos, placeholders, or missing pieces.

- **Code Quality**:
  - Provide concise comments for complex logic or Go idioms.
  - Offer testing suggestions using Go's `testing` package.

## 6. Rule Management and Organization

- **Rule Storage**: Rules are stored hierarchically in `.cursorrules/` (e.g., `.cursorrules/api/`, `.cursorrules/db/`).
- **Rule Fetching**: Fetch rules from `https://github.com/elie222/inbox-zero/tree/main/.cursor/rules` and map them to the `.cursorrules/` structure based on globs and descriptions.
- **Rule Application**: Read rules from `.cursorrules/` during generation and apply them to code implementation.

## 7. Development Workflow

- **Planning**:
  - Think step-by-step to design API structure, endpoints, and data flow.
  - Write detailed pseudocode before implementation (e.g., in comments or a separate file).

- **Example Pseudocode**:
  ```plaintext
  // Define API structure
  - Endpoint: GET /users
    - Handler: getUsers
    - Input: None
    - Output: JSON list of users
    - Steps:
      1. Validate request method
      2. Fetch users from database
      3. Marshal to JSON
      4. Return 200 OK with response

  // Confirm plan, then implement
  - Implementation:
    - Follow the confirmed plan to write secure, bug-free, efficient Go code.
    - Adhere to all API development guidelines.

## 8. User Stories

### As a Go Developer
I want automated cursor rules to enforce consistent API standards without manual setup.

### As a Team Lead
I want customizable rules to align with my team's API guidelines.

### As an IDE User
I want real-time linting feedback based on cursor rules.

### As an Open-Source Maintainer
I want to share rule sets with the community.

## 9. Success Metrics

| Metric | Target | Timeline |
|--------|--------|----------|
| Adoption | 100+ active users | 3 months |
| Performance | 95% of rule generations complete in under 2 seconds | Ongoing |
| Community Engagement | 10+ contributed rule sets | 6 months |
| Bug Reports | Fewer than 5 critical bugs | First month |

## 10. Cursor Rule Management for Go Projects

### How to Add or Edit Cursor Rules in a Go Project

1. **Rule File Location**
   - Place all rule files in:
     ```
     .cursorrules/
     ├── your-rule-name.mdc
     ├── another-rule.mdc
     └── ...
     ```
   - You may organize by category:
     ```
     .cursorrules/
     ├── api/
     │   ├── handler-naming.mdc
     │   └── error-handling.mdc
     ├── db/
     │   └── sql-injection-prevention.mdc
     └── ...
     ```

2. **Naming Convention**
   - Use kebab-case for filenames (e.g., `handler-naming.mdc`)
   - Use `.mdc` extension
   - Make names descriptive of the rule's purpose

3. **Directory Structure**
   ```
   PROJECT_ROOT/
   ├── .cursorrules/
   │   ├── api/
   │   │   └── handler-naming.mdc
   │   └── db/
   │       └── sql-injection-prevention.mdc
   └── ...
   ```

4. **Do NOT place rule files:**
   - In the project root
   - In subdirectories outside `.cursorrules/`
   - In any other location

5. **Cursor Rule File Structure**
   ```markdown
   ---
   description: Short description of the rule's purpose
globs: optional/path/pattern/**/*.go
alwaysApply: false
---
# Rule Title

Main content explaining the rule with markdown formatting.

1. Step-by-step instructions
2. Code examples
3. Guidelines

Example:
```golang
// Good example
func GoodHandler(w http.ResponseWriter, r *http.Request) {
    // Implementation following guidelines
}

// Bad example
func badhandler(w http.ResponseWriter, r *http.Request) {
    // Implementation not following guidelines
}
```

#### Example Go Utility Functions Rule

```markdown
---
description: Guidelines for creating and using utility functions in Go
globs: utils/**/*.go
alwaysApply: false
---
# Utility Functions in Go

- Place reusable logic in the `utils/` package.
- Use Go's standard library for common operations (e.g., `strings`, `sort`, `math`).
- For third-party utilities, prefer well-maintained packages and document their use.
- Keep utility functions small, focused, and well-documented.
- Write unit tests for all utility functions.

Example:
```go
// utils/slice.go

// Contains checks if a string is present in a slice.
func Contains(slice []string, item string) bool {
    for _, v := range slice {
        if v == item {
            return true
        }
    }
    return false
}
```
```

### How to Proceed for Generating Cursor Rules

1. **Define Core Categories**  
   Based on your PRD, start with categories like:
   - `api/` (API handler structure, error handling, middleware)
   - `db/` (database access, SQL injection prevention)
   - `utils/` (utility function guidelines)
   - `testing/` (test structure, coverage)
   - `project-structure/` (file/folder organization)

2. **Draft Initial Rule Files**  
   For each category, create `.mdc` files in `.cursorrules/` with:
   - A clear description
   - Relevant globs (e.g., `api/**/*.go`)
   - Markdown content with best practices, code examples, and step-by-step instructions

3. **Reference External Rules**  
   You can fetch and adapt rules from sources like [Inbox Zero .cursor rules](https://github.com/elie222/inbox-zero/tree/main/.cursor/rules) as inspiration, but tailor them for Go.

4. **Document the Rule Index**  
   Create a `README.md` or `index.mdc` in `.cursorrules/` listing all rules, their descriptions, and categories for easy navigation.

5. **Integrate with Tooling**  
   Ensure your rule generator reads from `.cursorrules/` and applies rules based on file globs and project structure.

6. **Iterate and Expand**  
   As your project grows, add new rules or refine existing ones based on team feedback and code review findings.

### Documentation and Onboarding
1. **Getting Started Guide**
   - Comprehensive `getting-started.md`
   - Step-by-step setup instructions
   - Best practices and common patterns
   - Troubleshooting guide

2. **Example Projects**
   - Sample Go API with pre-configured rules
   - Common use-case demonstrations
   - Rule customization examples

3. **CLI Wizard**
   - Interactive setup via `cursor-rules init`
   - Guided rule creation and configuration
   - Project structure validation

### Rule Customization and Validation
1. **Schema Validation**
   - JSON/YAML schemas for rule files
   - Automated validation on rule changes
   - Clear error messages for misconfigurations

2. **Custom Rule Development**
   - Templates for common rule types
   - Documentation for rule creation
   - Testing guidelines for custom rules

### Feedback and Iteration
1. **User Feedback Collection**
   - Built-in `cursor-rules feedback` command
   - Direct link to GitHub issues
   - Regular community surveys

2. **Continuous Improvement**
   - Monthly rule updates based on feedback
   - Community contribution guidelines
   - Regular documentation updates

## 10. Assumptions and Constraints
### 10.1 Assumptions
Users are familiar with Go and API development.

Tools like golangci-lint are installed.

### 10.2 Constraints
- Limited to Go in v1.0; no other languages.
- IDE Support Timeline:
  - Phase 1 (Months 1-3): VS Code integration
  - Phase 2 (Month 4-5): VS Code extension refinement
  - Phase 3 (Month 6): IntelliJ and GoLand support (v1.1)
  - Phase 4 (Month 7+): Additional IDE integrations based on user demand

## 11. Risks and Mitigation
Risk: Slow performance on large codebases.
Mitigation: Optimize algorithms, cache results.

Risk: Inconsistent IDE rule enforcement.
Mitigation: Use LSP, test across IDEs.

Risk: Low adoption.
Mitigation: Provide documentation, examples.

## 12. Timeline and Milestones
Month 1: Requirements, design, prototype.

Month 2: Core rule generation, linting integration.

Month 3: IDE plugins, testing.

Month 4: Beta release, feedback, fixes.

Month 5: v1.0 release.

## 13. Future Enhancements
Support for HTMX, gRPC, and other languages (e.g., TypeScript).

AI-driven rule suggestions.

Cloud-based rule storage.

## 14. Stakeholders
Developers: Go developers and teams.

Maintainers: Open-source contributors.

End Users: IDE users with cursor rules.

## 15. Approval
Author: [Your Name]

Reviewer: [Team Lead or Stakeholder]

Approval Date: [TBD]

## 16. Expert Review and Recommendations

### Strengths
- **Clear Purpose and Scope**: The tool's goals, audience, and integration points with Go's standard library and modern IDEs are well defined.
- **Best Practices**: Focus on Go idioms, RESTful design, and the use of `net/http` and `ServeMux` (Go 1.22+) ensures modern, idiomatic Go code.
- **Automation and Integration**: Integration with `golangci-lint`, `go fmt`, and `go vet` will catch most common errors and enforce style automatically.
- **Extensibility**: Support for custom/community rules and plugin architecture is forward-thinking and will help with long-term adoption.
- **Performance and Scalability**: Non-functional requirements are realistic and ambitious, ensuring the tool won't become a bottleneck.
- **Rule Management**: Hierarchical rule storage and external rule fetching are well thought out for maintainability and collaboration.
- **Workflow Guidance**: The step-by-step planning and pseudocode-first approach will help teams avoid common design and implementation errors.

### Recommendations for Further Improvement
- **Error Prevention**: Consider adding support for static code analysis tools that catch deeper issues (e.g., `staticcheck`, `errcheck`), or ensure these are included in your `golangci-lint` config. Encourage or automate the use of Go's race detector (`go test -race`) for concurrent code.
- **Productivity**: Ensure robust and well-documented LSP integration for real-time IDE feedback. Provide code actions or quick fixes in the IDE for common rule violations. Include sample `.cursorrules/` files and example rule sets for quick onboarding.
- **Testing and Quality**: Consider generating or scaffolding basic test files for new handlers/endpoints. Optionally, integrate with code coverage tools to encourage thorough testing.
- **Documentation and Onboarding**: Provide clear documentation, onboarding guides, and example projects. Consider a CLI wizard or interactive setup for first-time users.
- **Rule Customization**: Ensure that custom rule definitions are easy to write, validate, and debug. Provide schema validation and helpful error messages for misconfigured rules.
- **Feedback and Iteration**: Build in a feedback mechanism (e.g., CLI/IDE prompt or GitHub issues link) so users can easily report problems or suggest improvements.

**Conclusion:**
Your PRD sets a strong foundation for smooth, error-free, and productive Go API development. If you address the above considerations—especially around onboarding, testing, and rule customization—you will maximize the tool's impact and adoption. You are ready to proceed to rule creation. Iterate based on real-world feedback for best results.




