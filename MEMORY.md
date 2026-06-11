# StoreBuilder — MEMORY.md

## Architecture

- **Project**: UsahaKu MVP — AI-powered website generator for non-technical store owners
- **Brand name**: UsahaKu (formerly "StoreBuilder" in UI)
- **Location**: `d:\uhAHFSUBHSADBFnsa\storebuilder\`
- **Tech Stack**: Tailwind CSS (STITCH.md theme via CDN) + Vanilla JS — no build step, no server
- **Design System**: STITCH.md — Material Symbols icons, Inter font, primary #3525cd palette
- **AI**: Gemini API (`gemini-1.5-flash`) — product extraction, revision, full store data build
- **Persistence (generated site)**: `localStorage` only
- **Persistence (app state)**: none — stateless between sessions

## File Structure

```
storebuilder/
├── .gitignore             # Ignores .env
├── .env                   # Configuration for Flask backend
├── index.html             # 4-phase SPA dashboard (STITCH design system)
├── style.css              # Minimal — Tailwind handles everything
├── app.js                 # 4-phase state machine + Gemini API proxy calls
├── template-engine.js     # generateSite(storeData) → routes to selected template function
├── templates/
│   ├── toko-klasik.js     # Sidebar Classic template (Orders/Products/Accounting)
│   ├── dashboard-modern.js# Card-based modern Dark template
│   └── laporan-sederhana.js# White report-centric template
└── README.md
```

## Stable Decisions

| Decision | Value | Rationale |
|---|---|---|
| API key delivery | `.env` on Flask server | Backend proxy for security |
| Design system | STITCH.md (Tailwind + Material Symbols) | User requested |
| UI language | Indonesian | STITCH.md & user context |
| Dashboard structure | No header, no footer on landing (phase 1) | User requested |
| Chat flow | 3-step: product extraction → revision/approve → template select | User spec |
| Approve keywords | approve, setuju, ok, oke, yes, ya, lanjut, next, confirm | Case-insensitive |
| Template count | 3 skeleton wireframes (UX chooser) | User spec (reduced from 9) |
| Generated site themes | Colors from skeleton card dataset attributes | User spec |
| Generated site scope | Seller dashboard only (Orders, Products, Accounting) | User spec |
| Auto-prepopulation | Stock pre-loaded on boot with onboarding products | Premium UX |
| Deploy button | Stub modal only | MVP scope |

## 4-Phase App Flow

```
Phase 1: Landing (UsahaKu logo + chatbox only, no header/footer)
  ↓ User sends first message
  → Gemini extracts products + storeName + tagline (extractProducts())
  
  ↓ User chats to revise (→ Gemini reviseProducts())
  ↓ User types "approve" / clicks button
  
Phase 3: 3 Skeleton Template Chooser
  ↓ User clicks a card (saves selectedTemplate + colors)
  ↓ User clicks "Generate"
  → Gemini builds full storeData (buildStoreData())
  → generateSite(storeData) from template-engine.js
  
Phase 4: iframe preview + price banner + deploy stub
```

## Gemini Call Summary

| Function | Input | Output |
|---|---|---|
| `extractProducts(text)` | Raw user message | `{storeName, tagline, products:[{name,price}]}` |
| `reviseProducts(list, text)` | Current list + revision request | `[{name, price}]` |
| `buildStoreData()` | storeName, tagline, productList, selectedTemplate, colors | Full storeData JSON |

## Generated Site Template Contract

`generateSite(data)` → complete self-contained HTML string.
`data` shape:
```json
{
  "storeName": "", "tagline": "",
  "templateName": "",
  "products": [{"name": "", "price": "", "description": ""}],
  "primaryColor": "#hex", "accentColor": "#hex",
  "logoDataUrl": "",
  "contact": {"phone": "", "email": "", "address": ""},
  "social": {"instagram": "", "whatsapp": "", "tiktok": ""}
}
```
