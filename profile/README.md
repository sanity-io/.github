<div align="center">
  <img src="https://cdn.sanity.io/images/3do82whm/next/d6cf401d52c33b7a5a354a14ab7de94dea2f0c02-192x192.svg" alt="Sanity" width="160" />

# Sanity - Content Operating System

[![npm](https://img.shields.io/npm/v/sanity?style=flat-square)](https://www.npmjs.com/package/sanity)
[![npm downloads](https://img.shields.io/npm/dm/sanity?style=flat-square)](https://www.npmjs.com/package/sanity)
[![Discord](https://img.shields.io/discord/1304483263171264613?style=flat-square&logo=discord&label=discord)](https://www.sanity.io/community/join)
[![MIT License](https://img.shields.io/github/license/sanity-io/sanity?style=flat-square)](https://github.com/sanity-io/sanity/blob/main/LICENSE)

</div>

---

Sanity is a [Content Operating System][intro] that turns content into structured, reusable data. We give developers complete control over how content is modeled, managed, and delivered.

## Quick Links

🚀 [Get started][installation] • 📚 [Documentation][docs] • 💬 [Community][discord] • 🎓 [Learn][learn] • 📦 [Exchange][exchange]

## Why Developers Choose Sanity

- **[Content Lake][content-lake]**: Real-time database for structured content - query with [GROQ][groq], access via HTTP APIs from any language
- **[Schema-as-code][schemas]**: Define content models in TypeScript/JavaScript, version control them, get automatic [type generation][typegen]
- **[Real-time][realtime]**: Live queries, collaborative editing, instant previews built-in
- **[Customizable][studio-custom]**: React-based Studio you can customize completely, plus [App SDK][app-sdk] for organization-wide applications
- **Framework agnostic**: Works with Next.js, Remix, Astro, or any framework
- **[AI-ready][app-sdk]**: Structured content with rich context that AI can use effectively

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

Sanity powers content operations for teams at **Figma**, **Spotify**, **Shopify**, **Riot Games**, **Linear**, **Cloudflare**, **Netlify**, **Replit**, **PUMA**, **Nike**, **Supreme**, **Condé Nast**, **AT&T**, **Samsung**, and thousands more.

## Community & Resources

- 🔍 **Contribute**: Browse our [open source repositories][sanity-repo] and help build the platform
- 💬 **Connect**: Join our [community][discord] with thousands of developers
- 🎓 **Learn**: Free [courses and guides][learn] to master Sanity
- 📝 **Stay updated**: Read our [blog][blog] for releases and best practices
- 🔌 **Extend**: Browse [plugins and starters][exchange] on Sanity Exchange
- 💼 **Join us**: [We're hiring][careers] engineers to build the future of content

## Key Repositories

- **[sanity](https://github.com/sanity-io/sanity)**: The core Sanity toolkit, Studio, and CLI
- **[next-sanity](https://github.com/sanity-io/next-sanity)**: Sanity toolkit for Next.js
- **[GROQ](https://github.com/sanity-io/GROQ)**: Specification for the GROQ query language
- **[groq-js](https://github.com/sanity-io/groq-js)**: JavaScript implementation of GROQ
- **[visual-editing](https://github.com/sanity-io/visual-editing)**: Tools for live visual editing with Sanity
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
[installation]: https://www.sanity.io/docs/studio/installation
[pricing]: https://www.sanity.io/pricing
[sanity-repo]: https://github.com/sanity-io/sanity
[blog]: https://www.sanity.io/blog
[careers]: https://www.sanity.io/careers
[docs]: https://www.sanity.io/docs
[learn]: https://www.sanity.io/learn
[exchange]: https://www.sanity.io/exchange
[discord]: https://www.sanity.io/community/join
