# 🛍️ StoreBuilder – AI-Powered Website Generator for New Store Owners

## Project Overview

Build a web application that helps **non-technical store owners** create their own business website through a simple guided chat interface. The app uses the **Gemini API** to process user inputs and inject them into a pre-designed HTML template. The generated site includes three functional pages: **Orders**, **Stock**, and **Accounting**, all powered by `localStorage` (no backend required).

This is an **MVP** — the output is a live in-browser preview with a pricing tag and a "Deploy" button (deploy logic is a stub for now).

---

## Tech Stack

| Layer | Choice |
|---|---|
| Frontend Framework | Vanilla HTML/CSS/JS or React (your choice) |
| AI Integration | Gemini API (`gemini-1.5-flash` or `gemini-pro`) |
| Data Persistence (generated site) | `localStorage` |
| Template Rendering | Dynamic HTML injection |
| Deployment (stub) | Button UI only — no real deploy logic needed for MVP |

---

## Core User Flow

```
1. User lands on StoreBuilder homepage
2. A chat interface greets them and asks guided questions
3. Gemini API processes their answers and extracts structured data
4. User selects a visual theme (Minimal/Clean — MVP default)
5. A preview of their generated website is shown in-browser
6. Preview includes: price tag (e.g. "Free Preview / $9 to Deploy") + "Deploy" button
```

---

## Chat Interface — What to Collect

The chatbot must guide the user through collecting **all of the following** via natural conversation. Do NOT show a raw form — keep it conversational and friendly.

### Required Fields

| Field | Example |
|---|---|
| Store name | "Toko Maju Jaya" |
| Product list | "Baju batik, tas kulit, sendal anyaman" (with prices if provided) |
| Logo | Upload prompt or skip option |
| Color preference | "I like blue and white" or pick from swatches |
| Contact info | Phone number, email, address |
| Social media | Instagram handle, WhatsApp number, TikTok, etc. |

### Gemini API Role

Send the full conversation transcript to Gemini with a structured extraction prompt. Ask Gemini to return a **JSON object** with all fields normalized. Example output Gemini should return:

```json
{
  "storeName": "Toko Maju Jaya",
  "tagline": "Batik & Handcrafted Goods",
  "products": [
    { "name": "Baju Batik", "price": "Rp 150.000", "description": "Handmade batik shirt" }
  ],
  "primaryColor": "#1E3A5F",
  "accentColor": "#F5A623",
  "contact": {
    "phone": "+62 812-3456-7890",
    "email": "toko@email.com",
    "address": "Jl. Pahlawan No. 5, Semarang"
  },
  "social": {
    "instagram": "@tokobatik",
    "whatsapp": "+62 812-3456-7890"
  }
}
```

---

## Template — Minimal/Clean Theme

The generated website must be a **single HTML file** (self-contained, inline CSS + JS) with the following structure:

### Pages / Sections

#### 1. 🏠 Home / Landing Page
- Store name, tagline
- Hero section with color from user preference
- Product grid (name, price, short description, placeholder image)
- Contact info footer
- Social media links

#### 2. 📦 Orders Page
- Table showing: Order ID, Customer Name, Product, Qty, Status, Date
- Status options: Pending / Processing / Shipped / Done
- Add new order form
- All data stored in `localStorage` under key `storebuilder_orders`
- Filter by status

#### 3. 🗃️ Stock / Inventory Page
- Table showing: Product Name, SKU, Stock Qty, Price, Last Updated
- Add / Edit / Delete product entries
- Low stock warning (highlight rows where qty < threshold)
- All data stored in `localStorage` under key `storebuilder_stock`

#### 4. 💰 Accounting Page
- Income vs. Expense tracker
- Table: Date, Description, Type (Income/Expense), Amount
- Running balance shown at top
- Simple bar chart (pure JS canvas or CSS) showing monthly totals
- All data stored in `localStorage` under key `storebuilder_accounting`

### Navigation
- Fixed top navbar with store name/logo on the left
- Nav links: Home | Orders | Stock | Accounting
- Mobile-responsive (hamburger menu on small screens)

---

## Preview Mode (MVP Output)

After generation, show the website inside an **iframe or full-page preview** with:

### Price Tag Banner
- Positioned at the top of the preview (outside the iframe)
- Text: `"✨ Your website is ready! Free to preview. Deploy for $9/mo"`
- Style: clean pill badge, accent color background

### Deploy Button
- Large CTA button: `"🚀 Deploy My Website"`
- On click: show a modal — `"Coming soon! We'll notify you when deployment is available."`
- Optionally collect email for waitlist

### Download / Share (optional for MVP)
- "Copy HTML" button that copies the raw generated HTML to clipboard

---

## Gemini API Integration Details

### Chat Processing Prompt Template

```
You are a helpful assistant for a website builder app.
The user is a non-technical store owner who just answered a series of onboarding questions.
Here is the full chat transcript:

[TRANSCRIPT]

Extract the following information and return ONLY a valid JSON object (no markdown, no explanation):
- storeName
- tagline (generate one if not provided)
- products (array of {name, price, description})
- primaryColor (hex, infer from user preference or default to #2C3E50)
- accentColor (hex)
- contact {phone, email, address}
- social {instagram, whatsapp, tiktok}

If any field is missing, use a sensible placeholder or empty string.
```

### API Call Setup

```javascript
const response = await fetch("https://generativelanguage.googleapis.com/v1beta/models/gemini-1.5-flash:generateContent?key=YOUR_API_KEY", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({
    contents: [{ parts: [{ text: prompt }] }]
  })
});
```

> ⚠️ **API Key**: Accept the Gemini API key via a settings modal or `.env` config. Do NOT hardcode it.

---

## Chat UI Design Guidelines

- Minimal/Clean aesthetic: white background, soft shadows, sans-serif font (Inter or Poppins)
- Chat bubbles: user messages on the right (accent color), bot messages on the left (light gray)
- Typing indicator animation while Gemini is processing
- Progress bar or step indicator (e.g. "Step 3 of 6: Contact Info")
- Each question appears one at a time — do not dump all questions at once
- Support both **text input** and **quick-reply buttons** (e.g. color swatches, yes/no chips)

---

## File Structure (Suggested)

```
storebuilder/
├── index.html              # Main app (chat interface + template selector)
├── style.css               # App styles
├── app.js                  # Chat flow, Gemini API calls
├── template-engine.js      # Injects JSON data into HTML template string
├── templates/
│   └── minimal.js          # The Minimal/Clean template as a JS template literal
└── README.md
```

---

## MVP Scope — What's In vs. Out

| Feature | In MVP | Notes |
|---|---|---|
| Guided chat onboarding | ✅ | Full flow |
| Gemini API extraction | ✅ | JSON structured output |
| Minimal/Clean theme | ✅ | Only theme for now |
| Orders page (localStorage) | ✅ | |
| Stock page (localStorage) | ✅ | |
| Accounting page (localStorage) | ✅ | |
| In-browser preview | ✅ | |
| Price tag + Deploy button | ✅ | Deploy is a stub |
| Real deployment | ❌ | Future feature |
| Multiple themes | ❌ | Future: Bold, Corporate, Warm |
| User accounts / auth | ❌ | Future feature |
| Real payment integration | ❌ | Future feature |

---

## Success Criteria

- A store owner with zero coding knowledge can complete the chat in under 5 minutes
- The generated site preview looks professional and matches their brand colors
- All three management pages (Orders, Stock, Accounting) are functional using localStorage
- The "Deploy" button and price tag are clearly visible in the preview
- The app works fully in-browser with no server required (except Gemini API calls)

---

## Database Schema — Firebase Firestore

Since there are no user accounts yet, each session is identified by an **anonymous `sessionId`** (a UUID generated on first visit and persisted in `localStorage` under the key `storebuilder_session_id`). All Firestore documents are scoped under this ID.

### Collection Structure Overview

```
sessions/                         ← top-level collection
  {sessionId}/                    ← document per anonymous session
    ── (session metadata)
    products/                     ← subcollection: product list
      {productId}/
    chat_history/                 ← subcollection: chat messages
      {messageId}/
```

---

### 📄 Collection: `sessions`

**Path:** `sessions/{sessionId}`

Each document represents one anonymous builder session.

| Field | Type | Description |
|---|---|---|
| `sessionId` | `string` | UUID generated client-side on first visit |
| `createdAt` | `timestamp` | When the session was first created |
| `updatedAt` | `timestamp` | Last time any data was saved |
| `status` | `string` | `"onboarding"` \| `"preview"` \| `"completed"` |
| `storeName` | `string` | Extracted store name |
| `tagline` | `string` | Generated or user-provided tagline |
| `primaryColor` | `string` | Hex color, e.g. `"#1E3A5F"` |
| `accentColor` | `string` | Hex color, e.g. `"#F5A623"` |
| `logoUrl` | `string` | Firebase Storage URL or empty string |
| `contact` | `map` | `{ phone, email, address }` |
| `social` | `map` | `{ instagram, whatsapp, tiktok }` |
| `selectedTheme` | `string` | `"minimal"` (only option in MVP) |
| `generatedHtml` | `string` | Full generated HTML string (snapshot) |

**Example document:**
```json
{
  "sessionId": "a1b2c3d4-...",
  "createdAt": "2024-06-01T08:00:00Z",
  "updatedAt": "2024-06-01T08:12:00Z",
  "status": "preview",
  "storeName": "Toko Maju Jaya",
  "tagline": "Batik & Handcrafted Goods",
  "primaryColor": "#1E3A5F",
  "accentColor": "#F5A623",
  "logoUrl": "",
  "contact": {
    "phone": "+62 812-3456-7890",
    "email": "toko@email.com",
    "address": "Jl. Pahlawan No. 5, Semarang"
  },
  "social": {
    "instagram": "@tokobatik",
    "whatsapp": "+62 812-3456-7890",
    "tiktok": ""
  },
  "selectedTheme": "minimal",
  "generatedHtml": "<!DOCTYPE html>..."
}
```

---

### 📄 Subcollection: `sessions/{sessionId}/products`

**Path:** `sessions/{sessionId}/products/{productId}`

Stores the product list that was used to build the website. Saved after Gemini extracts it from the chat.

| Field | Type | Description |
|---|---|---|
| `productId` | `string` | Auto-generated Firestore document ID |
| `name` | `string` | Product name, e.g. `"Baju Batik"` |
| `price` | `string` | Price as string, e.g. `"Rp 150.000"` |
| `priceNumeric` | `number` | Numeric price for sorting/filtering, e.g. `150000` |
| `description` | `string` | Short product description |
| `imageUrl` | `string` | Firebase Storage URL or empty string |
| `order` | `number` | Display order in the product grid (0-indexed) |
| `createdAt` | `timestamp` | When this product was added |

**Example document:**
```json
{
  "productId": "prod_001",
  "name": "Baju Batik",
  "price": "Rp 150.000",
  "priceNumeric": 150000,
  "description": "Handmade batik shirt, available in S/M/L",
  "imageUrl": "",
  "order": 0,
  "createdAt": "2024-06-01T08:10:00Z"
}
```

---

### 📄 Subcollection: `sessions/{sessionId}/chat_history`

**Path:** `sessions/{sessionId}/chat_history/{messageId}`

Stores every message in the onboarding conversation — both bot questions and user answers. This allows resuming a session and replaying the chat for debugging or future personalization.

| Field | Type | Description |
|---|---|---|
| `messageId` | `string` | Auto-generated Firestore document ID |
| `role` | `string` | `"bot"` \| `"user"` |
| `content` | `string` | The message text |
| `step` | `string` | Which onboarding step this belongs to: `"store_name"` \| `"products"` \| `"logo"` \| `"colors"` \| `"contact"` \| `"social"` \| `"done"` |
| `timestamp` | `timestamp` | When the message was sent |
| `metadata` | `map` | Optional. For bot messages: `{ quickReplies: [...] }`. For user messages: `{ rawInput: "..." }` |

**Example documents:**
```json
[
  {
    "messageId": "msg_001",
    "role": "bot",
    "content": "Hi! What's the name of your store?",
    "step": "store_name",
    "timestamp": "2024-06-01T08:00:05Z",
    "metadata": {}
  },
  {
    "messageId": "msg_002",
    "role": "user",
    "content": "Toko Maju Jaya",
    "step": "store_name",
    "timestamp": "2024-06-01T08:00:20Z",
    "metadata": { "rawInput": "Toko Maju Jaya" }
  },
  {
    "messageId": "msg_003",
    "role": "bot",
    "content": "Great! Now tell me about your products and their prices.",
    "step": "products",
    "timestamp": "2024-06-01T08:00:21Z",
    "metadata": { "quickReplies": ["Add product", "Skip for now"] }
  }
]
```

---

### Firestore Security Rules

Since sessions are anonymous, scope all reads and writes to the `sessionId` stored client-side. No auth required for MVP.

```js
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {

    // Anyone can read/write their own session (identified by sessionId in the path)
    match /sessions/{sessionId} {
      allow read, write: if true; // MVP: open access; lock down when auth is added

      match /products/{productId} {
        allow read, write: if true;
      }

      match /chat_history/{messageId} {
        allow read, write: if true;
      }
    }
  }
}
```

> ⚠️ **Note:** The `allow: true` rules are intentionally permissive for MVP. When user authentication is added in a future iteration, replace with `request.auth.uid == sessionId` to scope access per user.

---

### Firestore Integration — Code Snippets

#### Initialize Firebase

```javascript
import { initializeApp } from "firebase/app";
import { getFirestore, doc, setDoc, addDoc, collection, getDocs, serverTimestamp } from "firebase/firestore";

const app = initializeApp({
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
});

const db = getFirestore(app);
```

#### Get or Create Session

```javascript
function getSessionId() {
  let id = localStorage.getItem("storebuilder_session_id");
  if (!id) {
    id = crypto.randomUUID();
    localStorage.setItem("storebuilder_session_id", id);
  }
  return id;
}
```

#### Save Session Data

```javascript
async function saveSession(data) {
  const sessionId = getSessionId();
  await setDoc(doc(db, "sessions", sessionId), {
    ...data,
    sessionId,
    updatedAt: serverTimestamp(),
  }, { merge: true }); // merge:true prevents overwriting existing fields
}
```

#### Save a Chat Message

```javascript
async function saveChatMessage({ role, content, step, metadata = {} }) {
  const sessionId = getSessionId();
  await addDoc(collection(db, "sessions", sessionId, "chat_history"), {
    role,
    content,
    step,
    metadata,
    timestamp: serverTimestamp(),
  });
}
```

#### Save Products (bulk replace after Gemini extraction)

```javascript
async function saveProducts(products) {
  const sessionId = getSessionId();
  const colRef = collection(db, "sessions", sessionId, "products");
  for (const [index, product] of products.entries()) {
    await addDoc(colRef, {
      ...product,
      order: index,
      createdAt: serverTimestamp(),
    });
  }
}
```

#### Load Full Session (to resume)

```javascript
async function loadSession() {
  const sessionId = getSessionId();
  const sessionDoc = await getDoc(doc(db, "sessions", sessionId));
  const products = await getDocs(collection(db, "sessions", sessionId, "products"));
  const chat = await getDocs(collection(db, "sessions", sessionId, "chat_history"));

  return {
    session: sessionDoc.exists() ? sessionDoc.data() : null,
    products: products.docs.map(d => d.data()).sort((a, b) => a.order - b.order),
    chatHistory: chat.docs.map(d => d.data()).sort((a, b) => a.timestamp - b.timestamp),
  };
}
```

---

### Updated Tech Stack

| Layer | Choice |
|---|---|
| Frontend Framework | Vanilla HTML/CSS/JS or React |
| AI Integration | Gemini API (`gemini-1.5-flash`) |
| Session Identity | Anonymous UUID via `localStorage` |
| **App Database** | **Firebase Firestore** |
| Data Persistence (generated site pages) | `localStorage` (Orders, Stock, Accounting) |
| Template Rendering | Dynamic HTML injection |
| Deployment (stub) | Button UI only |