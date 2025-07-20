# Clickmap Specification (v0.1)

Clickmap is a simple, structured format for describing the pages, UI elements, and user journeys of a website — enabling automated tools and AI agents to generate reliable browser test scripts with minimal human intervention.

## Key Concepts

- **Pages** – URLs and the elements on them.
- **Elements** – Each interactive UI element with multiple selectors.
- **LinksTo** – Defines page navigation.
- **Journeys** – High-level user flows described as sequential page/element steps.

## Format

The format is a single JSON file with two top-level keys:

- `pages`: all known pages and their selectors
- `journeys`: step-by-step sequences representing flows

See [`clickmap.schema.json`](../clickmap.schema.json) for details.
