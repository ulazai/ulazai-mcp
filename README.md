<img src="logo-400.png" alt="UlazAI Media logo" width="96" height="96">

# UlazAI Media MCP server

**Create private AI images with your UlazAI account: pick a model, confirm, generate, download.**

Remote MCP server: `https://mcp.ulazai.com/mcp` (Streamable HTTP) · Website: [ulazai.com](https://ulazai.com/)

## What it does

UlazAI Media lets an AI assistant create images through your UlazAI account. It first looks up which image models fit the request, saves the exact parameters as a quote, and starts one generation only after you confirm. It then polls until the private file is ready and gives you the link. Every write carries an idempotency key, so a retried call never creates a second image or spends a second credit.

Images are private to your account. The assistant checks your monthly allowance before it starts.

## Connect

- **Server URL:** `https://mcp.ulazai.com/mcp`
- **Transport:** Streamable HTTP
- **Authentication:** OAuth with PKCE (S256), dynamic client registration and client ID metadata documents, so MCP clients connect without manual setup. Sign-in runs through Auth0 with your UlazAI account.

**Claude (claude.ai, Desktop):** Settings → Connectors → Add custom connector → paste the server URL.

**Claude Code:**

```bash
claude mcp add --transport http ulazai https://mcp.ulazai.com/mcp
```

**Cursor, VS Code, Cline, Windsurf and other clients** (`mcp.json` / `cline_mcp_settings.json`):

```json
{
  "mcpServers": {
    "ulazai": {
      "type": "http",
      "url": "https://mcp.ulazai.com/mcp"
    }
  }
}
```

Cline uses `"type": "streamableHttp"`; see [llms-install.md](llms-install.md).

## Tools

| Tool | What it does |
|---|---|
| `get_ulazai_account` | Allowance and credits. |
| `search_ulazai_models` | Find image models that fit a request. |
| `prepare_ulazai_image` | Save prompt and parameters as a quote. |
| `create_ulazai_image` | Start the generation (after confirmation). |
| `get_ulazai_generation` | Status and private file link. |

## Example prompts

- Which model should I use for a product photo on a white background?
- Make a square hero image of a red bicycle against a brick wall.
- How many images can I still make this month?

## Links

- Website: https://ulazai.com/
- Documentation: https://ulazai.com/docs/
- Privacy policy: https://ulazai.com/privacy/
- Terms: https://ulazai.com/terms/
- Support: mailto:support@ulazai.com

## Keywords

AI image generator, text to image, product photo AI, model comparison, image generation API, marketing visuals, hero images.

Nederlands: AI afbeelding maken, AI plaatjes genereren, productfoto AI, beeld genereren, afbeeldingen voor website.

## More MCP servers by Samautomation

- [Scamchecker.nl](https://scamchecker.nl/): Check a suspicious email, SMS, WhatsApp message or link for scam signals (Netherlands, Belgium). ([listing](https://github.com/smrht/scamchecker-mcp))
- [Klussenbeheer](https://samdesk.nl/klussenbeheer/): Job management for Dutch service companies: jobs, customers, planning, quotes and invoices. ([listing](https://github.com/smrht/klussenbeheer-mcp))
- [Muziek maken met AI](https://muziekmakenmetai.nl/): Make an original song from a prompt or your own lyrics. Two versions per song, MP3 download. ([listing](https://github.com/smrht/muziekmakenmetai-mcp))
- [Beheer je WP](https://beheerjewp.nl/): Manage a WordPress site from your AI assistant: read, search, propose edits, Search Console data. ([listing](https://github.com/smrht/beheerjewp-mcp))
- [Backlinkswinkel](https://backlinkswinkel.nl/): Search Dutch websites for backlinks, check metrics and prices, order after confirmation, track. ([listing](https://github.com/smrht/backlinkswinkel-mcp))
- [Backlinksbeheer](https://backlinksbeheer.nl/): Read your stored backlinks, link checks and lost-link alerts per domain. Read-only. ([listing](https://github.com/smrht/backlinksbeheer-mcp))
- [Samautomation Video](https://samautomation.work/): Render an MP4 from your own images, clips, voice-over and timed captions. JSON to video. ([listing](https://github.com/smrht/samautomation-video-mcp))
- [PDF Samenvoegen](https://pdfsamenvoegen.nl/): Merge your own PDFs in a confirmed order and get one downloadable PDF. ([listing](https://github.com/smrht/pdfsamenvoegen-mcp))
- [Diamond Painting Converter](https://diamondpaintingconverter.com/): Find your purchased diamond painting patterns and download the PDF with DMC colour legend. ([listing](https://github.com/smrht/diamondpaintingconverter-mcp))
- [Nummerschilderen.com shop advisor](https://nummerschilderen.com/): Search paint-by-number kits, get size and price advice for your own photo, shop info. No login. ([listing](https://github.com/smrht/nummerschilderen-mcp))
- [DiamondPaintingWinkel.nl shop advisor](https://diamondpaintingwinkel.nl/): Search diamond painting kits, get size and price advice for your own photo, shop info. No login. ([listing](https://github.com/smrht/diamondpaintingwinkel-mcp))
- [AI Rechtshulp](https://ai-rechtshulp.nl/): Search Dutch and EU case law with ECLI sources and verify quotes against the judgment. ([listing](https://github.com/smrht/ai-rechtshulp-mcp))
- [SamDesk Support](https://samdesk.nl/support/plugin/): Read your SamDesk support inbox, find customer agreements and draft replies. Read-only. ([listing](https://github.com/smrht/samdesk-support-mcp))

## Publisher

Samautomation, Wognum, the Netherlands · https://samautomation.work

This repository holds the public listing (README, `server.json`, install notes). The server itself is hosted by the publisher; there is nothing to install or build.
