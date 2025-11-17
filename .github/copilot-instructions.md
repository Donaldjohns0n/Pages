# Copilot Instructions for Pages Repository

## Project Overview

The **Pages** repository (Master Quest Cognitive Scaffold Project) is a comprehensive documentation and framework system designed for orchestrating multi-agent AI workflows in consulting environments. This repository serves as both a reference architecture and implementation guide for building scalable AI consulting practices using micro-agent architectures. The primary audience includes AI architects, technical consultants, system integrators, and development teams building distributed AI agent systems for enterprise consulting scenarios.

## Tech Stack

This is primarily a **documentation and specification repository** with the following components:

- **Markdown (.md)**: All documentation files including blueprints, guides, and technical specifications
- **YAML (.yaml, .yml)**: Configuration schemas and registry manifests (e.g., `master_manifest.yaml`)
- **CSV (.csv)**: Structured data schemas for agent specifications and cataloging
- **Git**: Version control for documentation and framework evolution
- **No runtime code**: This repository contains no executable application code (no JavaScript, Python, Java, etc.)

### Key Technologies & Concepts
- **Micro-Agent Architecture**: Distributed AI agent system design patterns
- **Handoff Contracts**: Inter-agent communication protocols
- **Workflow Orchestration**: Task coordination and execution frameworks
- **Registry Systems**: Agent capability discovery and management
- **Meta-Logging**: System activity tracking and analytics

## Coding Guidelines

Since this is a documentation repository, follow these content and formatting standards:

### Documentation Standards

1. **Markdown Formatting**
   - Use ATX-style headers (`#`, `##`, `###`) consistently
   - Maintain consistent heading hierarchy without skipping levels
   - Use fenced code blocks with language identifiers (```yaml, ```markdown, etc.)
   - Use bullet points (`-`) for unordered lists and numbers (`1.`, `2.`) for ordered lists
   - Keep line length reasonable (aim for 120 characters max for readability)

2. **YAML Files**
   - Use 2-space indentation (no tabs)
   - Always quote string values that contain special characters
   - Include descriptive comments for complex structures
   - Follow the schema patterns established in `registry/master_manifest.yaml`
   - Validate YAML syntax before committing

3. **CSV Files**
   - Use comma separators consistently
   - Quote fields containing commas or special characters
   - Maintain consistent column order across all rows
   - Include header row with clear column names
   - Follow the schema established in `AI_Consulting_MicroAgents.csv`

4. **Content Consistency**
   - Maintain consistent terminology across all documents
   - Use "micro-agent" (hyphenated) when referring to individual agents
   - Use "Pages Framework" when referring to the orchestration system
   - Capitalize proper names: "Master Quest Cognitive Scaffold Project"
   - Use present tense for descriptions and imperatives for instructions

5. **Cross-References**
   - Use relative paths for internal links (e.g., `./docs/Pages_Blueprint.md`)
   - Ensure all referenced files exist before committing
   - Update related documentation when making structural changes
   - Maintain bidirectional links where appropriate

### File Naming Conventions

- Use `UPPER_SNAKE_CASE.md` for major architectural documents (e.g., `AI_CONSULTING_MICROAGENT_STACK.md`)
- Use `lowercase-kebab-case.md` for utility and supporting documents (e.g., `meta-log.md`)
- Use descriptive names that clearly indicate content purpose
- Avoid abbreviations unless widely understood in context

### Version Control Practices

- Write clear, descriptive commit messages in present tense
- Group related documentation changes in single commits
- Update the meta-log when making significant framework changes
- Maintain backward compatibility in schema definitions when possible

## Project Structure

```
/
├── .github/                          # GitHub configuration and Copilot instructions
│   └── copilot-instructions.md       # This file
├── docs/                             # Core framework documentation
│   └── Pages_Blueprint.md            # Master framework blueprint and architecture
├── registry/                         # Registry schemas and agent catalogs
│   └── master_manifest.yaml          # Central registry configuration schema
├── AI_CONSULTING_MICROAGENT_STACK.md # Comprehensive micro-agent documentation
├── AI_Consulting_MicroAgents.csv     # Structured agent specification data
├── 7_DAY_SPRINT_PLAN.md              # Implementation sprint guide
├── DEFAULT_PROMPT_STUBS.md           # Agent initialization templates
├── HANDOFF_CONTRACT_SCHEMA.md        # Inter-agent communication protocols
├── meta-log.md                       # System activity and orchestration log
└── README.md                         # Repository overview and quick start
```

### Key Directories

- **`/docs`**: Contains architectural blueprints and framework design documents
- **`/registry`**: Contains schema definitions and agent registry configurations
- **Root level**: Primary documentation files organized by topic and purpose

### Important Files

- **`master_manifest.yaml`**: Central registry schema defining agent, context, and workflow structures
- **`AI_CONSULTING_MICROAGENT_STACK.md`**: Complete micro-agent architecture with all 39 agents across 7 roles
- **`HANDOFF_CONTRACT_SCHEMA.md`**: Defines how agents communicate and exchange data
- **`Pages_Blueprint.md`**: Framework vision, orchestration workflow, and implementation phases
- **`meta-log.md`**: Chronological record of framework events and agent activities

## Testing Requirements

Since this is a documentation repository, traditional unit tests are not applicable. Instead, ensure quality through:

### Documentation Quality Checks

1. **Markdown Validation**
   - Verify all markdown syntax is valid
   - Check that all links resolve correctly
   - Ensure code blocks have proper language identifiers

2. **YAML Validation**
   - Validate YAML syntax using a YAML parser
   - Verify schema consistency with established patterns
   - Ensure all required fields are present

3. **CSV Validation**
   - Check that all rows have the same number of columns
   - Verify header row matches data columns
   - Ensure proper quoting and escaping

4. **Cross-Reference Validation**
   - Verify all internal links point to existing files
   - Check that referenced sections exist in target documents
   - Ensure schema references are accurate

5. **Content Review**
   - Verify technical accuracy of architectural descriptions
   - Check consistency of terminology across documents
   - Ensure examples are complete and correct
   - Validate that agent specifications include all required fields (Purpose, Inputs, Outputs, Triggers, Tools, KPIs)

### Pre-Commit Checklist

Before committing changes:
- [ ] All markdown files render correctly
- [ ] All YAML files parse without errors
- [ ] All CSV files have consistent structure
- [ ] All internal links are valid
- [ ] Terminology is consistent with existing documentation
- [ ] Related documents are updated to reflect changes
- [ ] Meta-log is updated for significant framework changes

## Special Considerations

### Micro-Agent Specifications

When adding or modifying micro-agent specifications, ensure each agent includes:
- **Role**: The high-level role category (1 of 7: Orchestration & Governance, Sales & Discovery, Data Intake & Mapping, Workflow Design, Implementation, Validation, Ops & Reporting)
- **Cluster**: The functional cluster within the role
- **Purpose**: Clear one-sentence description of agent responsibility
- **Inputs**: What the agent consumes
- **Outputs**: What the agent produces
- **Triggers**: Events that activate the agent
- **Tools**: Systems and platforms the agent uses
- **KPIs**: Measurable success metrics

### Handoff Contract Updates

When modifying handoff contract schemas, maintain:
- Backward compatibility where possible
- Clear versioning of schema changes
- Documentation of breaking changes
- Examples demonstrating new contract formats

### Registry Schema Changes

Changes to `master_manifest.yaml` should:
- Follow semantic versioning principles
- Document all new fields and structures
- Maintain compatibility with existing registry entries
- Update related documentation files

## Agent Collaboration Context

This repository supports a distributed micro-agent architecture where multiple AI agents work together. When making changes:

- Consider how changes affect agent discovery and registration
- Ensure context synchronization mechanisms remain clear
- Maintain workflow orchestration documentation accuracy
- Update meta-logging examples when adding new event types
- Keep handoff contract specifications complete and unambiguous

## Getting Started for Contributors

1. Read the **README.md** for project overview
2. Review **Pages_Blueprint.md** for framework architecture
3. Study **AI_CONSULTING_MICROAGENT_STACK.md** for agent details
4. Understand **HANDOFF_CONTRACT_SCHEMA.md** for integration patterns
5. Follow the **7_DAY_SPRINT_PLAN.md** for implementation guidance
6. Use **DEFAULT_PROMPT_STUBS.md** for agent initialization templates

When adding new content:
- Maintain consistency with existing documentation patterns
- Cross-reference related documents
- Update the meta-log for significant changes
- Follow the established file naming conventions
- Ensure all technical specifications are complete and accurate
