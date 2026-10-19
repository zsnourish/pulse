# Pulse docs

The documentation site for Pulse, Nourish's design system. It is built with Astro and Starlight, replaces the Pulse site in Supernova, and deploys to Netlify.

## What Pulse docs is the authority for

Pulse docs is the home for **shared design guidance**: what components mean and when to use them, foundations, content and language, and reusable patterns.

It is not the only source of truth. Other layers keep their own authority, and Pulse links to them rather than copying them:

| Concern | Authority |
|---|---|
| Shared design guidance and decisions | This repository |
| Visual definitions such as anatomy, variants, states and tokens | Pulse libraries in Figma |
| Web implementation | Pulse Components for Vue |
| Mobile implementation | Nourish Mobile UI |

> **Status:** this repository is moving to a private, Nourish-owned home. See the Federated Pulse Design Specification Architecture proposal in the Product Brain for the plan.

## How to edit a page

You don't need a local checkout.

1. Open the page on the site and select **Edit this page**. This opens the file in GitHub's web editor.
2. Make your change and choose **Create a new branch and start a pull request**.
3. Check the result in the pull request's Netlify deploy preview, if deploy previews are turned on for the site.
4. Someone else on the team reviews and approves it. Don't approve your own change.
5. When it merges into `main`, Netlify redeploys the site, usually within a minute.

Every page has a `status` in its frontmatter: `draft`, `in-review`, `approved` or `deprecated`. Merging a change doesn't make a page `approved` on its own. Change the status only when the content has been reviewed for that purpose.

### Do and Don't blocks

```html
<div class="ds-callout ds-do">
<p><strong>✓ Do</strong> — your guidance text.</p>
</div>
```

For the negative case, use `ds-dont` and `✗ Don't` instead.

## What's in here

- `src/content/docs/`: the pages. `foundations/`, `voice/`, `components/` and `docs/` (pages about the site itself) map to the sidebar groups set in `astro.config.mjs`.
- `src/content/config.ts`: the frontmatter schema, including `status`.
- `src/components/EditLinkWithHistory.astro`: adds a **View history** link next to **Edit this page**. Starlight's `lastUpdated` shows when each page last changed, read from git history.
- `public/scripts/ds-embed.js`: click-to-load embeds for Figma, Storybook and Confluence, so pages don't wait for heavy iframes.
- `src/pages/theme-studio.astro`: a standalone tool at `/theme-studio` for trying colour, font, spacing and corner settings with a live preview. It doesn't write to GitHub. Copy the CSS it generates into `src/styles/nourish-theme.css` through a pull request.
- `src/styles/nourish-theme.css`: Pulse brand tokens and site styling. Light theme only.
- `netlify.toml`: the Netlify build settings.

**Font note:** Pulse's heading font (FS Me) is licensed and not available here, so headings fall back to Inter Bold.

## Version history and recovery

Everything is in git, so every past version of every page can be recovered. See the **Version History** page on the site (`src/content/docs/docs/backups-and-history.mdx`).

## Local development (optional)

```
npm install
npm run dev
```

Run `npm run build` before opening a pull request that changes code or configuration.
