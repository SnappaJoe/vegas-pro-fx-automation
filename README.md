# vegas-pro-fx-automation
myles-vegas-fx-tools

## Regression Prevention Framework

This repository includes a comprehensive regression prevention system to ensure changes don't break existing functionality. **Silent breakage is unacceptable.**

### For Developers and Contributors

Before making ANY changes to scripts, review these documents:

1. **[Copilot Instructions](.github/copilot-instructions.md)** - Complete regression prevention guidelines
   - Checklist for identifying breaking changes
   - Edge case detection framework
   - Verification step templates
   - Response templates for change proposals

2. **[Regression Testing Checklist](.github/REGRESSION_TESTING_CHECKLIST.md)** - Testing template
   - Pre-change baseline testing
   - Post-change validation steps
   - Edge case test scenarios
   - Performance and UX testing

3. **[Common Pitfalls](.github/COMMON_PITFALLS.md)** - Quick reference guide
   - Frequent mistakes to avoid
   - Code patterns that cause regressions
   - Safety checks to always include
   - Quick decision trees

### Key Principles

- **Assume Casual Use**: Users run scripts without reading documentation
- **Fail Loudly**: Never silently fail or corrupt data
- **Preserve Projects**: Project files are sacred
- **Test Realistically**: Use real-world projects and scenarios

### Before Making Changes

1. Read the [Copilot Instructions](.github/copilot-instructions.md)
2. Complete the regression prevention checklist
3. Analyze potential breaking changes
4. Get approval before coding
5. Test thoroughly using the [Regression Testing Checklist](.github/REGRESSION_TESTING_CHECKLIST.md)

### When in Doubt

**Stop and ask questions.** It's better to clarify requirements than to silently break user workflows.
