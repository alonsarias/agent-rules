# Agent Rules

A collection of Cursor rules for AI-assisted development. Rules provide persistent guidance to help Cursor understand your preferred patterns, conventions, and best practices.

## Available Rule Sets

### React

Performance optimization and component architecture patterns adapted from [Vercel's agent-skills](https://github.com/vercel-labs/agent-skills) repository.

| Rule File | Description | Key Topics |
|-----------|-------------|------------|
| `react-composition-patterns.mdc` | Component architecture | Compound components, context, state management |
| `react-performance-critical.mdc` | Critical performance patterns | Async waterfalls, Promise.all, bundle size, lazy loading |
| `react-client-data-fetching.mdc` | Client-side data fetching | SWR, event listeners, localStorage |
| `react-rerender-optimization.mdc` | Re-render optimization | memo, useMemo, useState, useRef, derived state |
| `react-rendering-performance.mdc` | DOM/rendering performance | Animations, SVG, CSS content-visibility, conditionals |
| `react-javascript-performance.mdc` | JavaScript micro-optimizations | Loops, caching, Set/Map, array methods |
| `react-advanced-patterns.mdc` | Advanced React patterns | Refs, useEffectEvent, initialization |

**Attribution:** Based on Vercel Engineering's [agent-skills](https://github.com/vercel-labs/agent-skills), specifically `react-best-practices` and `composition-patterns`. Next.js-specific content has been removed to focus on pure React patterns.

---

## Installation

### Option 1: Copy to your project

```bash
# Clone this repository
git clone https://github.com/your-username/agent-rules.git

# Copy all rules to your project
cp -r agent-rules/.cursor/rules/ /path/to/your/project/.cursor/rules/

# Or copy only specific rule sets (e.g., React rules)
cp agent-rules/.cursor/rules/react-*.mdc /path/to/your/project/.cursor/rules/
```

### Option 2: Manual installation

1. Create a `.cursor/rules/` directory in your project root
2. Copy the `.mdc` files you want from this repository

### Option 3: Symlink (for multiple projects)

```bash
ln -s /path/to/agent-rules/.cursor/rules /path/to/your/project/.cursor/rules
```

---

## How Rules Work

Rules are automatically applied based on:

1. **Intelligent matching** - Cursor's AI determines relevance based on the rule's description
2. **File patterns** - Rules target specific file types via globs
3. **Manual invocation** - Mention a rule by name (e.g., `@react-performance-critical`)

All rules use `alwaysApply: false`, meaning they activate intelligently based on context rather than on every interaction.

### Usage Examples

**Automatic activation:**

```
"Why is my component re-rendering so much?"
→ react-rerender-optimization rules activate

"How should I structure this complex component?"
→ react-composition-patterns rules activate
```

**Manual invocation:**

```
@react-composition-patterns How should I refactor this component with many boolean props?
```

**View rules:** Open **Cursor Settings → Rules, Commands**.

---

## Customization

### Modify rule activation

Edit the `description` field in the frontmatter to change when rules activate:

```yaml
---
description: Your custom description with keywords for matching
globs: "*.tsx,*.jsx"
alwaysApply: false
---
```

### Add project-specific rules

Create additional `.mdc` files in `.cursor/rules/` for project-specific patterns.

### Enable always-on rules

Set `alwaysApply: true` for rules you want active on every interaction:

```yaml
---
alwaysApply: true
---
```

---

## File Format

Rules use the `.mdc` format with YAML frontmatter:

```markdown
---
description: Brief description with keywords for intelligent matching
globs: "*.tsx,*.jsx,*.ts,*.js"
alwaysApply: false
---

# Rule Title

Rule content in markdown format...
```

---

## References

- [Cursor Rules Documentation](https://cursor.com/docs/context/rules)
- [Vercel agent-skills Repository](https://github.com/vercel-labs/agent-skills)
- [React Documentation](https://react.dev)
