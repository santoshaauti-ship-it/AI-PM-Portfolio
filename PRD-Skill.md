# PRD-Skill.md - Product Requirement Document Writing Guide

## Overview
This document provides a standardized framework, best practices, and template for writing Product Requirement Documents (PRDs) for the Memory Game project. Use this guide to ensure consistency, clarity, and completeness across all PRDs.

---

## 1. PRD Structure & Sections

Every PRD should follow this hierarchical structure. Include all applicable sections for your feature:

### **Core Sections (Required)**
1. Executive Summary
2. Product Overview
3. Goals & Objectives
4. User Stories & Use Cases
5. Features & Requirements
6. Technical Architecture
7. Data Model
8. User Experience Flow
9. Success Metrics
10. Success Criteria (Definition of Done)
11. Approval & Sign-off

### **Supporting Sections (Recommended)**
- Timeline & Release Plan
- Constraints & Assumptions
- Risk Assessment
- Future Enhancements
- Implementation Notes

---

## 2. Detailed Section Guidelines

### 2.1 Executive Summary (100-150 words)
**Purpose**: High-level overview for stakeholders who won't read the full document.

**Should Include**:
- Product/Feature name
- Product type/category
- Target platform (web, mobile, desktop)
- Target users
- Primary goal/value proposition
- Key success metric

**Template**:
```
**Product Name:** [Feature or Product Name]
**Product Type:** [e.g., Web Feature, Mobile App, Enhancement]
**Platform:** [Browser-based, Native iOS, etc.]
**Target Users:** [Who will use this]
**Primary Goal:** [What problem does it solve]
```

---

### 2.2 Product Overview (200-300 words)
**Purpose**: Explain what the product is and why it matters.

**Should Include**:
- Clear product description (1-2 paragraphs)
- Key problems being solved
- Value propositions (3-5 bullet points)
- Differentiation from alternatives

**Template**:
```
### Description
[2-3 sentences about what the product/feature does]

### Key Value Propositions
- [Benefit 1] - [Why it matters]
- [Benefit 2] - [Why it matters]
- [Benefit 3] - [Why it matters]
```

---

### 2.3 Goals & Objectives
**Purpose**: Define measurable outcomes and strategic alignment.

**Structure**:
- **Short-term Goals** (3-6 months): Immediate deliverables
- **Long-term Goals** (6+ months): Strategic vision

**Best Practices**:
- Make goals SMART (Specific, Measurable, Achievable, Relevant, Time-bound)
- Align with product strategy
- Include 3-5 goals per timeframe

**Template**:
```
### Short-term Goals
1. [Specific goal with measurable outcome]
2. [Goal focused on immediate deliverables]
3. [Goal addressing user feedback]

### Long-term Goals
1. [Strategic expansion or feature growth]
2. [Market position or adoption goal]
```

---

### 2.4 User Stories & Use Cases
**Purpose**: Capture user perspectives and typical interaction patterns.

**User Story Format** (Use Agile format):
```
**User Story 1: [Persona Name]**
- *As a* [user type/role]
- *I want to* [action/capability]
- *So that* [benefit/value]
```

**Best Practices**:
- Write 3-5 primary user stories
- Include at least one story per major user segment
- Make acceptance criteria testable
- Include edge cases or alternative flows

**Template**:
```
**User Story 1: [Descriptive Title]**
- *As a* [specific user type]
- *I want to* [specific action]
- *So that* [specific benefit]

**Acceptance Criteria**:
- [ ] [Verifiable criterion]
- [ ] [Verifiable criterion]

**Alternative Flows**:
- [Edge case or alternate path]
```

---

### 2.5 Features & Requirements
**Purpose**: Detailed specification of what needs to be built.

**Structure**:
- Group related features under subsections (5.1, 5.2, etc.)
- Use checkbox format for trackability
- Specify exact values, colors, dimensions when applicable

**Best Practices**:
- Be specific and measurable
- Include technical specifications (e.g., colors in hex format)
- Reference standards or guidelines (WCAG, Material Design)
- Organize by priority or user journey
- Include edge cases and error handling

**Template**:
```
### 5.1 [Feature Category]

#### [Sub-feature Name]
- [ ] Specific requirement with quantifiable details
- [ ] Another requirement with technical specs
- [ ] Edge case handling requirement
```

**Examples of Good Requirements**:
```
✅ "Toast notification displays for 3 seconds before auto-dismissing"
✅ "Button hover state changes from #2196f3 to #1565c0"
✅ "Form validation triggers after user leaves input field (blur event)"

❌ "Make notifications work" (too vague)
❌ "Use nice colors" (not measurable)
❌ "Handle errors gracefully" (undefined behavior)
```

---

### 2.6 Technical Architecture
**Purpose**: Outline technical decisions and constraints.

**Should Include**:
- Tech stack / Programming languages
- Architecture patterns (MVC, MVVM, etc.)
- Key libraries and dependencies
- Browser/device compatibility
- Performance targets

**Template**:
```
### Tech Stack
- **Frontend:** [Languages/Frameworks]
- **Backend:** [If applicable]
- **Storage:** [Database/Cache technology]
- **External Services:** [APIs, CDNs, etc.]

### Browser Compatibility
- [ ] Chrome 90+
- [ ] Firefox 88+
- [ ] Safari 14+
- [ ] Mobile browsers
```

---

### 2.7 Data Model
**Purpose**: Specify how data is structured and stored.

**Best Practices**:
- Use pseudocode or JSON format
- Show relationships between entities
- Include field names and types
- Specify storage location (client, server, cache)

**Template**:
```
### [Entity Name]
```json
{
  "fieldName": "type",
  "nestedField": {
    "property": "type",
    "optional": "type | null"
  }
}
```

### localStorage Schema
```json
{
  "keyName": "value",
  "userPreferences": {
    "theme": "light | dark",
    "notifications": "boolean"
  }
}
```
```

---

### 2.8 User Experience Flow
**Purpose**: Describe the step-by-step user journey.

**Best Practices**:
- Number each step sequentially
- Use action verbs (User clicks, System displays, etc.)
- Include decision points and branches
- Reference feature names from Section 5

**Template**:
```
1. **Page Load** - [What happens on load]
2. **User Action** - [What user does]
3. **System Response** - [What system displays]
4. **Confirmation** - [How user knows action succeeded]
5. **Next State** - [What options are available next]
```

---

### 2.9 Success Metrics
**Purpose**: Define how to measure feature success.

**Categories**:
- **User Engagement**: Session duration, feature usage rate, retention
- **Performance**: Load times, response times, error rates
- **Business**: Adoption rate, revenue impact, user satisfaction
- **Quality**: Bug report rate, accessibility compliance

**Template**:
```
### User Engagement
- [ ] Feature used by >30% of active users
- [ ] Average session time increases by 15%

### Performance
- [ ] Page load time < 2 seconds
- [ ] Feature interaction < 500ms response time

### Quality
- [ ] Zero critical bugs on release
- [ ] WCAG AA compliance achieved
```

---

### 2.10 Success Criteria (Definition of Done)
**Purpose**: Clear checklist for feature completion.

**Best Practices**:
- Make all items binary (yes/no, done/not done)
- Include testing, documentation, and accessibility
- Link to requirements sections
- Include code quality standards

**Template**:
```
- [ ] All features from Section 5 implemented
- [ ] Unit tests written with >80% code coverage
- [ ] Accessibility audit passed (WCAG AA)
- [ ] Cross-browser testing completed
- [ ] Performance benchmarks met
- [ ] Documentation written and reviewed
- [ ] Code review approved by 2+ team members
```

---

## 3. Optional But Recommended Sections

### 3.1 Timeline & Release Plan
```
| Phase | Duration | Deliverables |
|-------|----------|--------------|
| **Design** | X days | [What's delivered] |
| **Dev** | X days | [What's delivered] |
| **Testing** | X days | [What's delivered] |
| **Release** | X days | [What's delivered] |
```

### 3.2 Constraints & Assumptions
```
### Constraints
- [Technical limitation]
- [Budget/resource limitation]

### Assumptions
- [What we're assuming about users/systems]
- [External dependencies we're relying on]
```

### 3.3 Risk Assessment
```
| Risk | Impact | Probability | Mitigation |
|------|--------|-------------|-----------|
| [Risk] | High/Medium/Low | High/Med/Low | [How to prevent/handle] |
```

### 3.4 Future Enhancements
```
### Phase 2 Features
- [ ] [Feature idea]

### Phase 3 Features
- [ ] [Feature idea]
```

---

## 4. Writing Best Practices

### ✅ Do's
- **Be specific**: Use exact values, colors (hex codes), dimensions
- **Be measurable**: Include numbers, thresholds, percentages
- **Be consistent**: Use same terminology throughout document
- **Use examples**: Show mockups, code snippets, screenshots
- **Use checklists**: Make requirements trackable with [ ]
- **Reference sections**: "See Section 5.2 for details"
- **Consider edge cases**: What happens when things go wrong?
- **Think accessibility**: Include WCAG compliance requirements
- **Write for stakeholders**: Use language non-technical readers understand
- **Keep it current**: Update as understanding evolves

### ❌ Don'ts
- **Don't be vague**: "Make it nice" or "handle errors" are not requirements
- **Don't assume**: State assumptions explicitly
- **Don't overspecify UI**: Leave design decisions to designers
- **Don't forget edge cases**: Consider error states, slow networks, etc.
- **Don't mix concerns**: Keep technical details separate from user flows
- **Don't ignore performance**: Always think about speed and scalability
- **Don't forget accessibility**: Accessibility is not optional
- **Don't write novels**: Keep sections focused and concise
- **Don't skip sections**: Completeness matters

---

## 5. Examples of Strong Requirements vs Weak Ones

### Bad (Vague)
```
"Add a settings feature for users to customize their experience"
```

### Good (Specific & Measurable)
```
### 5.3 Settings Panel

#### Theme Selection
- [ ] Dropdown menu with "Light" and "Dark" options
- [ ] Default theme: "Light"
- [ ] Theme preference stored in localStorage
- [ ] Theme applies to all UI elements within 100ms
- [ ] CSS transition duration: 0.3s for smooth switching
```

---

## 6. Common Feature Types & Templates

### Feature Type A: UI Component
**Focus on**: Appearance, interaction, accessibility

```
- Visual specifications (colors, dimensions, typography)
- Interaction patterns (hover, click, focus states)
- Keyboard navigation requirements
- Screen reader labels and announcements
- Mobile responsiveness details
```

### Feature Type B: Integration/API
**Focus on**: Data flow, error handling, security

```
- Request/response schemas
- Error codes and handling
- Authentication/authorization
- Rate limiting
- Data validation rules
```

### Feature Type C: Performance Optimization
**Focus on**: Metrics, benchmarks, testing

```
- Current baseline metrics
- Target improvements
- Measurement methodology
- Performance testing approach
- Acceptable trade-offs
```

---

## 7. PRD Document Naming Convention

```
PRD-[FeatureName].md

Examples:
- PRD.md (main product PRD)
- PRD-DarkTheme.md
- PRD-Leaderboard.md
- PRD-SoundEffects.md
- PRD-Multiplayer.md
```

---

## 8. Review Checklist

Use this before submitting your PRD:

**Content Completeness**
- [ ] Executive summary present and compelling
- [ ] All 11 core sections completed
- [ ] User stories include acceptance criteria
- [ ] Requirements are specific and measurable
- [ ] Success metrics are quantifiable
- [ ] Data models documented with examples

**Quality & Clarity**
- [ ] No grammatical errors or typos
- [ ] Technical jargon explained or avoided
- [ ] Consistent terminology throughout
- [ ] Section references are correct
- [ ] Examples and mockups included where helpful

**Feasibility**
- [ ] Requirements are realistically achievable
- [ ] Timeline is reasonable
- [ ] Team has necessary skills/resources
- [ ] Risks identified and mitigated
- [ ] Dependencies clearly stated

**Stakeholder Alignment**
- [ ] Product/engineering leadership reviewed
- [ ] Design team consulted
- [ ] QA input incorporated
- [ ] Business goals aligned
- [ ] User feedback considered

---

## 9. Quick Start Template

Copy and paste this template for new PRD documents:

```markdown
# [Product/Feature Name] - Product Requirement Document (PRD)

## 1. Executive Summary

**Product Name:** [Feature Name]
**Product Type:** [Type]
**Platform:** [Platform]
**Target Users:** [Users]
**Primary Goal:** [Goal]

---

## 2. Product Overview

### Description
[Description]

### Key Value Propositions
- [Benefit 1]
- [Benefit 2]
- [Benefit 3]

---

## 3. Goals & Objectives

### Short-term Goals
1. [Goal]
2. [Goal]

### Long-term Goals
1. [Goal]
2. [Goal]

---

## 4. User Stories & Use Cases

**User Story 1: [Name]**
- *As a* [user]
- *I want to* [action]
- *So that* [benefit]

---

## 5. Features & Requirements

### 5.1 [Feature Category]
- [ ] [Requirement]
- [ ] [Requirement]

---

## 6. Technical Architecture

### Tech Stack
- [Technology]

### Browser Compatibility
- [ ] Chrome 90+
- [ ] Firefox 88+

---

## 7. Data Model

[JSON schema]

---

## 8. User Experience Flow

1. [Step]
2. [Step]

---

## 9. Success Metrics

### Engagement
- [ ] [Metric]

### Performance
- [ ] [Metric]

---

## 10. Success Criteria

- [ ] [Criterion]
- [ ] [Criterion]

---

## 11. Approval & Sign-off

| Role | Name | Date |
|------|------|------|
| PO | | |
| Tech Lead | | |

---

**Document Version:** 1.0
**Last Updated:** [Date]
**Status:** APPROVED FOR DEVELOPMENT
```

---

## 10. Tips for Effective PRDs

1. **Write for your audience**: Non-technical stakeholders need simpler language; engineers need detailed specs
2. **Use visuals**: Include wireframes, mockups, screenshots, or diagrams where helpful
3. **Iterate**: PRDs evolve—update them as understanding improves
4. **Be collaborative**: Review with team before finalizing
5. **Stay focused**: One PRD per feature/product—don't combine unrelated items
6. **Include examples**: Show what good looks like
7. **Document decisions**: Explain the "why" behind requirements
8. **Plan for change**: Include a mechanism for tracking PRD versions
9. **Make it searchable**: Use clear headings and keywords
10. **Link to resources**: Reference related documents, designs, specs

---

## 11. References & Resources

- [Agile Alliance - User Stories](https://www.agilealliance.org/)
- [WCAG 2.1 Accessibility Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)
- [Atlassian - Agile Requirements](https://www.atlassian.com/agile)
- [Prodpad - PRD Template](https://www.prodpad.com/)

---

**Last Updated**: April 26, 2026  
**Version**: 1.0  
**Maintained By**: Memory Game Product Team
