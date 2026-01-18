---
description: Generate and update comprehensive documentation for developers and product managers
allowed-tools: Read, Write, Bash, Grep, Glob
---

# Generate Documentation

You are generating comprehensive documentation for two audiences: developers and product managers.

## Process

### Phase 1: Analyze the Repository

1. **Get repository overview**
````bash
   git log --oneline -20
   git branch --show-current
   ls -la
````

2. **Analyze codebase structure**
````bash
   find . -type f -name "*.js" -o -name "*.py" -o -name "*.java" | head -50
   cat package.json || cat requirements.txt || cat pom.xml
   cat README.md
````

3. **Check for existing documentation**
````bash
   ls -la *.md
   cat CHANGELOG.md 2>/dev/null || echo "No changelog"
````

### Phase 2: Generate Developer Documentation

1. **Load developer documentation skill**
   - Use the `doc-developer` skill
   - Read `.claude/skills/doc-developer/SKILL_DOC_DEVELOPER.md`

2. **Analyze technical aspects**
   - Technology stack and dependencies
   - Code structure and architecture
   - API endpoints and modules
   - Database schema (if applicable)
   - Testing setup
   - Deployment configuration

3. **Generate DOCUMENTATION_DEVELOPER.md**
   - Follow structure from SKILL_DOC_DEVELOPER.md
   - Include:
     - Architecture overview
     - Setup instructions
     - Code structure
     - API documentation
     - Testing guide
     - Deployment guide
     - Troubleshooting

4. **Update if exists, create if new**
   - If DOCUMENTATION_DEVELOPER.md exists, update with latest changes
   - If new, create from scratch
   - Preserve custom sections marked with `<!-- CUSTOM -->`

### Phase 3: Generate Product Manager Documentation

1. **Load PM documentation skill**
   - Use the `doc-pm` skill
   - Read `.claude/skills/doc-pm/SKILL_DOC_PM.md`

2. **Analyze product aspects**
   - Features and capabilities
   - User-facing functionality
   - Recent changes and releases
   - Integration points
   - Business value

3. **Generate DOCUMENTATION_PM.md**
   - Follow structure from SKILL_DOC_PM.md
   - Include:
     - Product overview
     - Features and use cases
     - User journeys
     - Metrics (if available)
     - Release history
     - Roadmap (if available)
     - Getting started guide

4. **Update if exists, create if new**
   - If DOCUMENTATION_PM.md exists, update with latest changes
   - If new, create from scratch
   - Preserve custom sections marked with `<!-- CUSTOM -->`

### Phase 4: Summary

After generating both documents, provide a summary:
````markdown
## Documentation Generated ✅

### DOCUMENTATION_DEVELOPER.md
- [Updated/Created]
- Sections: [count]
- Key updates: [summary]

### DOCUMENTATION_PM.md
- [Updated/Created]
- Sections: [count]
- Key updates: [summary]

### Next Steps
- Review both documents for accuracy
- Add custom sections if needed (mark with <!-- CUSTOM -->)
- Commit to repository
- Share with team
````

## Tips

### For Developer Documentation
- Be comprehensive with technical details
- Include actual code examples from the repo
- Document all setup steps
- Explain architecture decisions
- Keep API docs updated

### For PM Documentation
- Focus on user value and business impact
- Use clear, non-technical language
- Highlight recent changes and improvements
- Include metrics when available
- Make it scannable with clear sections

### Preserving Custom Content
Both skills support custom sections. If users add:
````markdown
<!-- CUSTOM -->
## Our Special Process
[Custom content]
<!-- /CUSTOM -->
````

These sections will be preserved during updates.

### Version Control
After generation:
````bash
git add DOCUMENTATION_DEVELOPER.md DOCUMENTATION_PM.md
git commit -m "docs: update documentation"
````

