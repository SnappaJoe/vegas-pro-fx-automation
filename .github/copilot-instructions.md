# GitHub Copilot Instructions Template

Use this template to translate human intent into precise, actionable instructions for GitHub Copilot.

---

## Instructions for [Feature/Fix Name]

### 🎯 Objective
[Clear, concise statement of what needs to be accomplished]

---

### ⚠️ What MUST NOT Change
- **DO NOT** modify [specific files, functions, or components that must remain unchanged]
- **DO NOT** alter [existing behavior, APIs, or interfaces that other code depends on]
- **DO NOT** remove [critical functionality, error handling, or security checks]
- **DO NOT** change [configuration files, database schemas, or deployment scripts] unless explicitly required
- **PRESERVE** all existing [tests, documentation, backwards compatibility]

---

### 📋 Scope
**What IS included:**
- [Specific files, modules, or components to modify]
- [Features to add or update]
- [Bug fixes or improvements to implement]

**What is NOT included:**
- [Related but out-of-scope work]
- [Future enhancements to defer]
- [Dependencies or infrastructure changes not needed]

**Constraints:**
- Language/Framework: [e.g., C#, Python, React]
- Code style: [Follow existing patterns in the codebase]
- Dependencies: [Only add if absolutely necessary]
- Performance: [Any performance requirements or limitations]

---

### ✅ Success Criteria
The implementation is complete when:
- [ ] [Specific, measurable outcome 1]
- [ ] [Specific, measurable outcome 2]
- [ ] All existing tests pass
- [ ] New tests added for new functionality (if applicable)
- [ ] Code follows existing style and patterns
- [ ] Documentation updated (if applicable)
- [ ] No regression in existing features
- [ ] [Any other verification steps]

---

### 📝 Additional Context
[Optional: Include relevant background, examples, or links to issues/PRs]

---

## Usage Instructions

1. Copy the template above
2. Fill in each section with specific details for your task
3. Paste directly into GitHub Copilot Chat
4. Review Copilot's proposed changes against the success criteria
5. Verify that constraints in "What MUST NOT Change" are respected
