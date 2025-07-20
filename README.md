# Clickmap

**Clickmap** is a lightweight, open JSON-based format that describes a website’s structure, UI element selectors, and user journeys. It is designed to be used by humans, AI agents, or test automation tools to generate reliable, fully automated browser-based test flows — with zero or minimal manual intervention.

> Think of it as a combination of a sitemap, UI map, and user flow spec — all in one.

## 🚀 What Problem Does Clickmap Solve?

Creating and maintaining automated end-to-end (E2E) browser test scripts is time-consuming and fragile:

- QA engineers have to **inspect DOMs** to find stable selectors  
- Developers **don't annotate flows or links**  
- LLM agents struggle with **web page discovery and element targeting**  
- Tests break due to **UI changes or poor element identification**

Clickmap solves this by providing:

✅ A **structured map** of all known pages  
✅ A list of **UI elements** on each page, with selectors  
✅ A definition of **page-to-page links**  
✅ A set of **user journeys** (E2E flows)  

With this, human testers or LLMs can generate automation scripts in any framework (e.g., Cypress, Playwright, Selenium, Maestro, Patrol) — fully programmatically.

---

## 🧠 Use Cases

- ✅ **AI test generation**: Generate automation test cases using AI agents (e.g. GPT-4, Claude)
- ✅ **Framework-agnostic**: Drive Playwright/Cypress/Selenium scripts using Clickmap as input
- ✅ **Collaboration layer**: Use as a shared test flow definition between devs, QAs, and tools
- ✅ **Scaffold test suites**: Define test coverage from shared JSON across teams or pipelines
- ✅ **Robustness**: Reduce test flakiness by defining robust selectors and links
- ✅ **CI-ready**: Enable CI pipelines to spin up test coverage from a Clickmap file
- ✅ **Reverse engineer test flows**: Build automation for existing websites by generating Clickmaps for any page and sharing them with other testers, teams, or tools

---

## 📦 How It Works

Clickmap uses a single JSON file with two main sections:

### 1. `pages[]`

Each page defines:

- a unique `id`
- a `url` (absolute or relative)
- a list of `elements` with `name` and multiple `selectors`
- optionally, a list of `linksTo` other `pageId`s

### 2. `journeys[]`

Each journey describes a **high-level E2E user flow** (no loops or logic) by referencing pages and UI elements in sequence.

---

## 🔧 Example

```json
{
  "pages": [
    {
      "id": "homepage",
      "url": "https://example.com",
      "elements": [
        {
          "name": "Book Now Button",
          "selectors": ["#book-now", ".cta-button"]
        }
      ],
      "linksTo": ["signup"]
    },
    {
      "id": "signup",
      "url": "https://example.com/signup",
      "elements": [
        {
          "name": "Email Input",
          "selectors": ["#email"]
        },
        {
          "name": "Continue Button",
          "selectors": ["button[type=submit]"]
        }
      ],
      "linksTo": ["confirmation"]
    }
  ],
  "journeys": [
    {
      "name": "New User Room Booking",
      "steps": [
        { "pageId": "homepage", "elementName": "Book Now Button" },
        { "pageId": "signup", "elementName": "Email Input" },
        { "pageId": "signup", "elementName": "Continue Button" }
      ]
    }
  ]
}
```
## 🛠 Tooling Support

Clickmap is designed to work with a variety of tools and workflows:

- ✅ Human-authored specs (JSON)
- ✅ Generated via browser extension, LLM, or scraper
- ✅ Interpreted by AI agents to generate tests
- ✅ Read by custom test runners or pipelines

## 🌍 Goals

- Simple and lightweight format
- Encourages collaboration between QAs, devs, and AI tools
- Friendly to versioning and code review
- Enables zero-manual-setup automation test creation

## 📁 Repo Structure

```
clickmap/
├── clickmap.schema.json # JSON Schema definition
├── examples/
│ └── room-booking.clickmap.json
├── docs/
│ └── spec.md # Human-readable format guide
└── README.md # This file
```

## 📅 Roadmap

- [x] v0.1 JSON Schema  
- [ ] Browser extension to auto-generate Clickmap  
- [ ] CLI tool to validate/generate Clickmaps  
- [ ] AI agent integration (OpenAI, Claude, etc.)  
- [ ] VSCode extension support  

## 📖 Learn More

- 📘 [Specification](./docs/spec.md)  
- 📂 [Schema File](./clickmap.schema.json)  
- 🧪 [Examples](./examples)

## 🪪 License

MIT — free to use, extend, and adapt.  
