<div align="center">
  <img src="https://cdn.sanity.io/images/3do82whm/next/d6cf401d52c33b7a5a354a14ab7de94dea2f0c02-192x192.svg" alt="Sanity" width="160" />

# Sanity - Content Operating System

[![npm](https://img.shields.io/npm/v/sanity?style=flat-square)](https://www.npmjs.com/package/sanity)
[![npm downloads](https://img.shields.io/npm/dm/sanity?style=flat-square)](https://www.npmjs.com/package/sanity)
[![Discord](https://img.shields.io/discord/1304483263171264613?style=flat-square&logo=discord&label=discord)](https://www.sanity.io/community/join)
[![MIT License](https://img.shields.io/github/license/sanity-io/sanity?style=flat-square)](https://github.com/sanity-io/sanity/blob/main/LICENSE)

</div>

---

Sanity is the [Content Operating System][intro] for the AI era. Model your content as code, store it in a real-time API, and use it everywhere: websites, mobile apps, agentic applications, and the editorial workflows in between.

## Quick Links

🚀 [Get started][installation] • 📚 [Documentation][docs] • 💬 [Community][discord] • 🎓 [Learn][learn] • 📦 [Exchange][exchange]

## Why Developers Choose Sanity

- **[Content Lake][content-lake]**: Real-time database for structured content. Query with [GROQ][groq], or access it over HTTP from any language.
- **[Schema-as-code][schemas]**: Define content models in TypeScript, version control them, and get automatic [type generation][typegen] for queries and documents.
- **Real-time and collaborative**: Live queries, multiplayer editing, and instant previews are part of the platform.
- **[Studio][studio-custom] + [App SDK][app-sdk]**: A customizable React-based editorial environment, plus an SDK with hooks and stores for building custom content apps on top of Sanity.
- **AI agents and content automation**: The [MCP server][mcp] lets Claude, Cursor, and VS Code read and edit your content with full schema context. [Agent Actions][agent-actions] generate, transform, and translate content with LLMs. [Canvas][canvas] turns free-form drafts into structured documents.
- **[Functions][functions]**: Serverless logic that runs on content changes. No infrastructure to maintain.
- **Framework agnostic**: Works with Next.js, Astro, Nuxt, React Router, SvelteKit, or any framework.

<details>
<summary>See code examples</summary>

### Schema-as-code

```typescript
// schemaTypes/articleType.ts
import { defineType, defineField } from "sanity";

export const articleType = defineType({
  name: "article",
  type: "document",
  fields: [
    defineField({
      name: "title",
      type: "string",
      validation: (Rule) => [
        Rule.required(),
        Rule.max(80).warning(
          "Titles over 80 characters may be truncated in search results"
        ),
      ],
    }),
    defineField({
      name: "excerpt",
      type: "text",
      validation: (Rule) =>
        Rule.custom((value, context) => {
          // Cross-field validation
          const isFeatured = context.document?.featured;
          return isFeatured && !value
            ? "Featured articles need an excerpt"
            : true;
        }),
    }),
  ],
});
```

### GROQ query language

```typescript
import { defineQuery } from "groq";

export const ARTICLES_QUERY = defineQuery(`*[_type == "article"] {
  _id,
  title,
  "author": author->name,
  "categories": categories[]->title,
  "wordCount": length(pt::text(body))
}[0...10]`);
```

[GraphQL][graphql] is also available if you prefer it.

</details>

## Getting Started

```bash
npm create sanity@latest
```

This [creates a Sanity project][installation] with Studio and connects you to the Content Lake. You'll get:

- A customizable content management interface
- Real-time APIs for your content
- Automatic TypeScript types
- Generous free tier with hosting and bandwidth included (no credit card required)

**Pricing**: Start free, pay-as-you-go for overages. [View pricing →][pricing]

## Trusted By

Sanity powers content operations for teams at **Spotify**, **Shopify**, **Figma**, **Unity**, **Linear**, **Anthropic**, **MoMA**, **Brex**, **Arc'teryx**, **Tecovas**, and thousands more.

## Community & Resources

- 🔍 **Contribute**: Browse our [open source repositories][sanity-repo] and help build the platform
- 💬 **Connect**: Join our [community][discord] with thousands of developers
- 🎓 **Learn**: Free [courses and guides][learn] to master Sanity
- 📝 **Stay updated**: Read our [blog][blog] for releases and best practices
- 🔌 **Extend**: Browse [plugins and starters][exchange] on Sanity Exchange
- 💼 **Join us**: [We're hiring][careers] engineers to build the future of content

## Key Repositories

- **[sanity](https://github.com/sanity-io/sanity)**: Core toolkit, Studio, and CLI
- **[sdk](https://github.com/sanity-io/sdk)**: App SDK for building custom content applications on top of Sanity
- **[next-sanity](https://github.com/sanity-io/next-sanity)**: Sanity toolkit for Next.js
- **[agent-toolkit](https://github.com/sanity-io/agent-toolkit)**: Building blocks for AI agents working with Sanity content
- **[visual-editing](https://github.com/sanity-io/visual-editing)**: Tools for live visual editing
- **[GROQ](https://github.com/sanity-io/GROQ)**: Specification for the GROQ query language
- **[groq-js](https://github.com/sanity-io/groq-js)**: JavaScript implementation of GROQ
- **[document-internationalization](https://github.com/sanity-io/document-internationalization)**: Plugin for translating documents across languages

## Contributing

We welcome contributions to our open source projects. Check each repository's CONTRIBUTING.md for guidelines, or report bugs in the relevant issue tracker.

---

**Built by developers, for developers.** We treat content as a strategic asset and give technical teams the tools to work without constraints.

[intro]: https://www.sanity.io/docs/getting-started/the-sanity-content-operating-system-an-introduction
[content-lake]: https://www.sanity.io/docs/content-lake
[documents]: https://www.sanity.io/docs/content-lake/documents
[groq]: https://www.sanity.io/docs/content-lake/groq-introduction
[schemas]: https://www.sanity.io/docs/apis-and-sdks/introduction-to-schemas
[typegen]: https://www.sanity.io/docs/apis-and-sdks/sanity-typegen
[graphql]: https://www.sanity.io/docs/content-lake/graphql
[realtime]: https://www.sanity.io/docs/content-lake/realtime-updates
[studio-custom]: https://www.sanity.io/docs/studio/studio-customization
[app-sdk]: https://www.sanity.io/docs/app-sdk/sdk-introduction
[agent-actions]: https://www.sanity.io/docs/agent-actions
[mcp]: https://www.sanity.io/docs/ai/mcp-server
[canvas]: https://www.sanity.io/canvas
[functions]: https://www.sanity.io/docs/functions
[installation]: https://www.sanity.io/docs/sanity-studio-quickstart/setting-up-your-studio
[pricing]: https://www.sanity.io/pricing
[sanity-repo]: https://github.com/sanity-io/sanity
[blog]: https://www.sanity.io/blog
[careers]: https://www.sanity.io/careers
[docs]: https://www.sanity.io/docs
[learn]: https://www.sanity.io/learn
[exchange]: https://www.sanity.io/exchange
[discord]: https://www.sanity.io/community/join
