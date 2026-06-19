# DESIGN.md for AI UI Agents: A Practical Way to Share Design Taste

[getdesign.md](https://getdesign.md/) is a public collection of DESIGN.md files made for AI coding agents. It takes recognizable product aesthetics and turns them into agent-readable design system analysis: patterns, tokens, component rules, layout behavior, and the reasoning behind the interface.

That matters because AI tools do not need more vague design inspiration. They need concrete design memory. getdesign.md gives them that memory in a format they can actually use before generating UI.

At the time of writing, the site includes dozens of DESIGN.md references across categories like AI and LLM platforms, developer tools, backend and DevOps products, productivity software, fintech, ecommerce, media, automotive, and creative tools. You can find design directions inspired by products such as Vercel, Linear, Stripe, Notion, Supabase, Figma, Apple, Airbnb, Shopify, Cursor, Raycast, and many more.

The useful part is not that these references exist as a gallery. The useful part is that each one tries to translate visible interface decisions into a reusable design language. Instead of telling an agent "make it look like Vercel," you can hand it a Vercel-inspired DESIGN.md and let it read the color roles, typography rules, spacing logic, components, and responsive behavior.

AI tools are getting better at writing frontend code, but they still struggle with one thing teams care about every day: taste. Ask an agent to create a dashboard, landing page, or product screen and the result may be functional, responsive, and polished enough at first glance. The problem is that it often feels anonymous.

That is the gap DESIGN.md tries to close.

A DESIGN.md file is a plain markdown document that explains a visual system to an AI coding agent. It gives the agent the same kind of context a designer would normally carry in their head: color roles, typography choices, spacing habits, component behavior, responsive rules, and the reasoning behind them.

The idea was popularized by Google Stitch, where a markdown-based design description can guide UI generation without requiring a Figma plugin, a proprietary token format, or a giant prompt. The format is simple enough to keep in a repository, but structured enough for an agent to use before it writes code.

That is why the format works well as both documentation and input. A human can read it as a design brief; an agent can read it as operating context.

## Why AI-generated interfaces look familiar

Most AI-generated UI has a recognizable pattern. Soft cards, large rounded corners, pastel gradients, centered hero sections, generic navigation, and a primary button that could belong to almost any SaaS product.

That happens because the agent is optimizing for a broad idea of "good interface design." It knows common patterns, but it does not automatically know your product's visual logic. It does not know whether your brand should feel spare and technical, editorial and spacious, dense and operational, playful and animated, or quiet and infrastructure-like.

You can try to fix this with longer prompts:

- Use this exact blue for links.
- Keep cards flat.
- Use a 1px border instead of shadows.
- Make headings lighter.
- Keep spacing tighter on data-heavy pages.
- Avoid marketing-style hero sections.

That works once, maybe. Then you have to repeat it in the next prompt, and the next page, and every future component. Eventually the prompt becomes a fragile design manual pasted into chat.

Screenshots are not a complete answer either. A screenshot can show what a page looked like in one state, but it does not explain the system underneath it. It does not tell the agent when to use an accent color, which spacing scale to follow, how a card behaves on mobile, or why a button should feel restrained instead of loud.

DESIGN.md turns that implicit knowledge into a durable file.

## What a DESIGN.md file actually does

Think of DESIGN.md as a design brief written for machines and humans at the same time. It is not only a list of tokens. It is a combination of exact values and practical judgment.

A good DESIGN.md file answers questions like:

- What is the dominant surface color?
- Which color is reserved for primary action?
- How heavy should headings feel?
- Are cards separated by shadows, borders, tint, or whitespace?
- How wide can the main content area become?
- What happens to grids and navigation on small screens?
- Which component patterns are part of the system?
- Which parts of the system are unknown or intentionally undocumented?

The important part is that these answers are semantic. A color is not just `#000000`; it might be `ink`, used for primary text and high-emphasis UI. A border is not just `#e5e5e5`; it might be `hairline`, used to create structure without visual noise. A button is not just padding and a background color; it has a role, tone, state behavior, and place in the interface.

That semantic layer is what helps an AI agent make better decisions when the exact situation was not described in advance.

## Why markdown is a strong format for this

Markdown is not glamorous, but it is practical. It is easy to read, easy to diff, easy to version, and easy for AI agents to consume. That matters more than it sounds.

Design systems often live in places agents cannot use directly. Figma files are visual and interactive, but an agent writing code usually cannot inspect the full design intent from them. Token exports are precise, but they often lose the human explanation. Brand guideline PDFs may describe the mood beautifully, but they rarely contain the concrete implementation rules an agent needs.

Markdown sits between those worlds.

It can hold structured values, prose rationale, tables, code snippets, component notes, and responsive behavior in one file. A developer can review it in a pull request. A designer can improve the wording. An AI agent can read it before generating UI.

That makes DESIGN.md especially useful in AI-assisted development, where the goal is not simply to store design tokens, but to transfer judgment.

## The difference between tokens and design language

Tokens are useful, but tokens alone are not enough.

If an agent sees this:

```yaml
colors:
  primary: "#0070F3"
  background: "#FFFFFF"
  border: "#EAEAEA"
```

it knows three values. It still does not know the personality of the interface. It does not know whether the primary color should appear everywhere or only in decisive moments. It does not know whether the background should feel clinical, editorial, premium, dense, or playful.

Now compare that with a DESIGN.md-style explanation:

```markdown
Primary blue is reserved for intentional action: submit buttons, active links,
and focused navigation states. Do not use it as decoration. Most of the page
should remain white, black, and hairline gray so the product feels fast,
technical, and exact.
```

The second version gives the agent a policy, not just a value. That policy is what keeps future screens consistent.

## What belongs inside DESIGN.md

The strongest DESIGN.md files usually combine structured front matter with prose sections. The structure may vary, but the core ingredients are consistent.

### 1. A short system overview

The overview should explain the visual direction in plain language. This is where the file says what the interface should feel like and what tradeoffs define it.

For example:

```markdown
This system favors precision over decoration. Surfaces stay flat, hierarchy
comes from spacing and type scale, and the accent color appears only when the
user needs to act.
```

That kind of sentence gives an agent a useful mental model before it touches a component.

### 2. Color roles

Colors should be named by responsibility, not by appearance alone. `primary`, `ink`, `muted`, `surface`, `canvas`, `border`, `danger`, and `success` are more useful than `blue-1` or `gray-4` because the name explains where the color belongs.

Each role should include the exact value and a short usage note:

```yaml
colors:
  accent: "#FF5A1F"
  ink: "#111111"
  muted: "#666666"
  canvas: "#FAFAFA"
  surface: "#FFFFFF"
  line: "#E6E6E6"
```

Then the prose should explain the intent:

```markdown
Accent is used for primary action and active states only. It should not be
used for large decorative backgrounds because the brand should feel sharp,
not saturated.
```

### 3. Typography rules

Typography needs more than font names. A useful DESIGN.md describes scale, weight, line height, letter spacing, and usage.

It should answer:

- Which type style is used for display headlines?
- How dense should body copy feel?
- Are headings heavy, neutral, or lightweight?
- Does the interface rely on large type or compact hierarchy?
- What fallback fonts should be used if the primary face is unavailable?

AI agents often default to oversized headings and dramatic spacing. Clear typography rules stop that from happening.

### 4. Layout and spacing

Spacing is one of the fastest ways to make AI-generated UI feel either coherent or generic. A DESIGN.md file should define a spacing scale and explain how it is used.

For example, a content site may use generous section spacing and narrow reading widths. A developer dashboard may need denser rows, tighter controls, and compact toolbars. Both can be "well designed," but they should not use the same rhythm.

Good layout guidance includes:

- Page container widths
- Grid behavior
- Section spacing
- Toolbar density
- Sidebar or navigation rules
- Empty-state spacing
- Mobile collapse behavior

### 5. Components

Components are where the design system becomes practical. A DESIGN.md should describe reusable UI pieces in terms of the tokens and principles already defined.

Instead of saying "make a nice button," it should define:

- Primary button
- Secondary button
- Icon button
- Card
- Input
- Badge
- Navigation item
- Modal
- Table row

Each component should include surface, typography, padding, radius, border, state behavior, and accessibility expectations where relevant.

The goal is not to replace a component library. The goal is to make sure the agent builds or modifies components in the same visual language each time.

### 6. Responsive behavior

Responsive design cannot be left to guesswork. Agents are good at making things stack, but stacking alone is not a responsive strategy.

A useful DESIGN.md describes what changes across breakpoints:

- When navigation collapses
- How many columns grids use
- Which controls move into menus
- How section spacing changes
- Whether sidebars become drawers
- What touch target sizes are required

This helps the agent preserve the design system on mobile instead of simply shrinking the desktop layout.

### 7. Known gaps

One underrated section is "Known Gaps." It tells the agent what the file does not define.

That might include:

- Dark mode
- Chart colors
- Animation timing
- Empty states
- Error states
- Marketing pages
- Email templates

Stating gaps is useful because it prevents false confidence. If dark mode is not documented, the agent should not invent a complete dark theme and pretend it belongs to the system.

## How getdesign.md helps

Most teams do not start from a blank design language. They reference products they already understand:

- "Make this feel closer to Vercel."
- "Use the restraint of Linear."
- "Give it some Stripe-like clarity."
- "Keep it as clean as Notion."
- "Make the app feel more like Supabase or Figma."

Those references are common because they are efficient. The trouble is that they are vague when handed to an AI agent.

getdesign.md turns those visual references into DESIGN.md files that agents can actually read. Each file captures observable patterns from a product aesthetic and translates them into a reusable design brief.

The purpose is not to copy another company pixel for pixel. It is to start from a recognizable design language, then adapt it to your own product. The file gives the agent a better starting point than a generic prompt.

## A practical workflow

The workflow is intentionally simple:

1. Choose a DESIGN.md file that matches the direction you want.
2. Place it in your project or paste it into your agent context.
3. Tell the agent to read the file before making UI changes.
4. Build the first screen.
5. Adjust the DESIGN.md file when you notice a recurring rule.
6. Keep the file versioned with the rest of the codebase.

Over time, DESIGN.md becomes less like a prompt and more like project infrastructure. It documents the design language in a place where both humans and agents can use it.

## What DESIGN.md is not

DESIGN.md is not a magic theme engine. Dropping the file into a repo will not automatically restyle an app. The implementation still has to happen in React, CSS, Tailwind, native components, or whatever stack the project uses.

It is also not a replacement for product design. It cannot decide what your product should do, what your users need, or whether a workflow is clear. It helps with consistency, translation, and design memory.

It is not a legal brand guideline document either. Many DESIGN.md files are inspired by public visual patterns, not official systems. Brand names and trademarks remain the property of their owners.

The best way to treat DESIGN.md is as an agent-readable design contract. It says, "When you make UI in this project, these are the visual rules and the reasons behind them."

## Why this matters for AI-assisted frontend work

AI agents are becoming part of everyday product development. They can create components, refactor layouts, wire up states, and move quickly across a codebase. But speed without design memory creates inconsistency.

One page gets shadows. Another gets borders. One screen uses large editorial spacing. Another becomes dense and cramped. One prompt says "minimal," the next says "premium," and the interface slowly loses direction.

DESIGN.md gives the agent a stable reference point.

It lets a team say:

- This is how our product should feel.
- These are the tokens that matter.
- These are the components we trust.
- These are the responsive rules.
- These are the areas that still need design decisions.

That is valuable whether you are using Claude Code, Cursor, Windsurf, Codex, or another AI coding environment. The exact tool matters less than the shared file the tool can read.

## Final thought

The future of design systems for AI will not be only visual, and it will not be only tokens. Agents need values, rules, examples, and rationale in the same place.

That is what DESIGN.md provides: a small, readable file that turns taste into usable context.

For teams building with AI, that context can be the difference between a page that merely looks acceptable and an interface that actually feels like it belongs to the product.

## Disclaimer

DESIGN.md files inspired by public products are educational references, not official brand systems. They document visible interface patterns and should be adapted with care for each project.
