# TESTS.md â€” StoreBuilder Canonical Test Registry
# APPEND-ONLY. Never delete or mutate entries. Mark retired tests as deprecated.

[TEST]
id: T-001
timestamp: 2026-06-11T12:49:27+07:00
scope: storebuilder/index.html + storebuilder/config.js
type: unit
description: Inline warning banner is shown when config.js still has the placeholder key "YOUR_API_KEY_HERE"
inputs: CONFIG.GEMINI_API_KEY = "YOUR_API_KEY_HERE"
expected: A visible red/orange banner appears at top of page with text directing user to edit config.js; chat input is disabled
status: pending
linked_change:

[TEST]
id: T-002
timestamp: 2026-06-11T12:49:27+07:00
scope: storebuilder/index.html + storebuilder/config.js
type: unit
description: Chat starts normally when config.js has a real (non-placeholder) API key value
inputs: CONFIG.GEMINI_API_KEY = "AIza..." (any non-placeholder string)
expected: No warning banner; chat shows Step 1 greeting message
status: pending
linked_change:

[TEST]
id: T-003
timestamp: 2026-06-11T12:49:27+07:00
scope: storebuilder/app.js (ChatFlow)
type: unit
description: Chat starts with Step 1 greeting after page load with valid API key
inputs: Page load with valid CONFIG.GEMINI_API_KEY
expected: Bot message "Hi! I'm StoreBuilder..." appears; step indicator shows "Step 1 of 6"
status: pending
linked_change:

[TEST]
id: T-004
timestamp: 2026-06-11T12:49:27+07:00
scope: storebuilder/app.js (ChatFlow)
type: unit
description: Each chat step appears only after the previous step's answer is submitted
inputs: User submits answer to Step 1
expected: Step 2 question appears; step indicator advances to "Step 2 of 6"
status: pending
linked_change:

[TEST]
id: T-005
timestamp: 2026-06-11T12:49:27+07:00
scope: storebuilder/app.js (sendToGemini)
type: unit
description: Typing indicator (3-dot bounce) is visible while Gemini API call is in-flight
inputs: All 6 steps completed; Gemini fetch pending
expected: Typing indicator appears in chat; input is disabled during processing
status: pending
linked_change:

[TEST]
id: T-006
timestamp: 2026-06-11T12:49:27+07:00
scope: storebuilder/app.js (sendToGemini)
type: integration
description: Gemini API response is parsed as valid JSON with all required fields
inputs: Valid API key; completed 6-step transcript
expected: Parsed object has keys: storeName, tagline, products, primaryColor, accentColor, contact, social
status: pending
linked_change:

[TEST]
id: T-007
timestamp: 2026-06-11T12:49:27+07:00
scope: storebuilder/template-engine.js + templates/minimal.js
type: integration
description: Generated site HTML contains the store name provided by user
inputs: storeData.storeName = "Test Store"
expected: Generated HTML string contains "Test Store" in the nav/hero section
status: pending
linked_change:

[TEST]
id: T-008
timestamp: 2026-06-11T12:49:27+07:00
scope: storebuilder/template-engine.js + templates/minimal.js
type: integration
description: Generated site HTML contains the correct primary and accent colors
inputs: storeData.primaryColor = "#1E3A5F", storeData.accentColor = "#F5A623"
expected: Generated HTML contains both hex values in inline CSS (CSS custom properties or direct style)
status: pending
linked_change:

[TEST]
id: T-009
timestamp: 2026-06-11T12:49:27+07:00
scope: templates/minimal.js (Orders page)
type: integration
description: Orders page in generated site adds an order and persists it in localStorage
inputs: Fill add-order form in generated site, submit
expected: New row appears in orders table; localStorage key "storebuilder_orders" contains the new order on page reload
status: pending
linked_change:

[TEST]
id: T-010
timestamp: 2026-06-11T12:49:27+07:00
scope: templates/minimal.js (Stock page)
type: integration
description: Stock page supports add, edit, and delete of products with localStorage persistence
inputs: Add a product, edit its price, delete a different product
expected: Table updates correctly; localStorage key "storebuilder_stock" reflects all changes after each action
status: pending
linked_change:

[TEST]
id: T-011
timestamp: 2026-06-11T12:49:27+07:00
scope: templates/minimal.js (Accounting page)
type: integration
description: Accounting page calculates and displays the correct running balance
inputs: Add 2 income entries (500, 300) and 1 expense entry (200)
expected: Running balance displayed = 600; table shows all 3 rows
status: pending
linked_change:

[TEST]
id: T-012
timestamp: 2026-06-11T12:49:27+07:00
scope: templates/minimal.js (Accounting page â€” bar chart)
type: unit
description: Monthly bar chart renders on Canvas when at least one accounting entry exists
inputs: 1 accounting entry in current month
expected: Canvas element is visible and non-empty (has at least one colored bar)
status: pending
linked_change:

[TEST]
id: T-013
timestamp: 2026-06-11T12:49:27+07:00
scope: storebuilder/index.html (preview section)
type: unit
description: Preview banner shows the correct price/CTA text after site generation
inputs: Site generation completes
expected: Banner text contains "Free to preview" and "Deploy for $9"
status: pending
linked_change:

[TEST]
id: T-014
timestamp: 2026-06-11T12:49:27+07:00
scope: storebuilder/index.html (Deploy button)
type: unit
description: Clicking the Deploy button opens a "Coming soon" modal
inputs: Click "Deploy My Website" button
expected: Modal appears with "Coming soon" message; optionally shows email input for waitlist
status: pending
linked_change:

[TEST]
id: T-015
timestamp: 2026-06-11T12:49:27+07:00
scope: storebuilder/index.html (Copy HTML button)
type: unit
description: "Copy HTML" button copies the generated HTML string to the clipboard
inputs: Click "Copy HTML" button after site generation
expected: navigator.clipboard.writeText is called with the full generated HTML; button shows "Copied!" feedback
status: pending
linked_change:

[TEST]
id: T-016
timestamp: 2026-06-11T12:49:27+07:00
scope: templates/minimal.js (responsive layout)
type: unit
description: Generated site shows hamburger menu at 375px viewport width
inputs: Open generated site in browser; resize to 375px wide
expected: Hamburger icon visible; desktop nav links hidden; clicking hamburger toggles the nav
status: pending
linked_change:

[TEST]
id: T-017
timestamp: 2026-06-11T12:49:27+07:00
scope: storebuilder/app.js (logo upload step)
type: unit
description: Uploading a logo image converts it to base64 and it appears in the generated site
inputs: Upload any JPEG/PNG in Step 3 (Logo)
expected: Generated site hero/nav shows the uploaded image (src starts with "data:image/")
status: pending
linked_change:

[TEST]
id: T-018
timestamp: 2026-06-11T12:49:27+07:00
scope: storebuilder/app.js (logo skip step)
type: unit
description: Skipping the logo prompt results in a placeholder/initials avatar in the generated site
inputs: Click "Skip" in Step 3 (Logo)
expected: Generated site shows store initials or a placeholder avatar in place of a logo
status: pending
linked_change:

[TEST]
id: T-019
timestamp: 2026-06-11T13:15:57+07:00
scope: storebuilder/index.html (phase 1)
type: unit
description: Phase 1 shows ONLY UsahaKu branding, chatbox, and guidelines — no header or footer visible
inputs: Open index.html in browser
expected: Only logo/title 'UsahaKu', subtitle, guideline pills, example button, and chatbox are visible; no nav header or page footer
status: pending
linked_change: 2026-06-11T13:15:57+07:00

[TEST]
id: T-020
timestamp: 2026-06-11T13:15:57+07:00
scope: storebuilder/app.js (extractProducts)
type: integration
description: Sending first product message transitions app to phase 2 and shows a product table
inputs: Type "Saya jual Baju Batik Rp 150.000 dan Tas Kulit Rp 350.000" and send
expected: Phase 2 appears; product table shows 2 rows: Baju Batik / Rp 150.000 and Tas Kulit / Rp 350.000
status: pending
linked_change: 2026-06-11T13:15:57+07:00

[TEST]
id: T-021
timestamp: 2026-06-11T13:15:57+07:00
scope: storebuilder/app.js (reviseProducts)
type: unit
description: Typing a revision in phase 2 chat updates the product table
inputs: In phase 2, type "ubah harga Baju Batik menjadi Rp 200.000"
expected: Product table row for Baju Batik updates to Rp 200.000; AI confirms revision in chat
status: pending
linked_change: 2026-06-11T13:15:57+07:00

[TEST]
id: T-022
timestamp: 2026-06-11T13:15:57+07:00
scope: storebuilder/app.js (phase transition)
type: unit
description: Typing "approve" in phase 2 transitions to phase 3 skeleton chooser
inputs: Type "approve" in phase 2 input
expected: Phase 3 view appears showing 9 skeleton template cards
status: pending
linked_change: 2026-06-11T13:15:57+07:00

[TEST]
id: T-023
timestamp: 2026-06-11T13:15:57+07:00
scope: storebuilder/index.html (phase 3)
type: unit
description: Exactly 9 skeleton template cards are shown in phase 3
inputs: Reach phase 3
expected: 9 cards visible in 3x3 grid: Modern Agency, Minimal Portfolio, Corporate Landing, Dashboard Sidebar, E-Commerce Grid, Personal Brand, Blog Article, SaaS Landing, Event RSVP
status: deprecated
deprecation_reason: Reduced to 3 seller-only templates as per user request
linked_change: 2026-06-11T13:15:57+07:00

[TEST]
id: T-024
timestamp: 2026-06-11T13:15:57+07:00
scope: storebuilder/app.js (selectTemplate)
type: unit
description: Clicking a skeleton card selects it (visual selection indicator shown)
inputs: Click 'E-Commerce Grid' card
expected: Card shows selected state (blue border, blue shadow, check icon visible); other cards deselected
status: pending
linked_change: 2026-06-11T13:15:57+07:00

[TEST]
id: T-025
timestamp: 2026-06-11T13:15:57+07:00
scope: storebuilder/app.js (handleGenerate)
type: integration
description: Clicking 'Generate' without selecting a template shows warning message
inputs: Click 'Buat Website Sekarang' without selecting a card
expected: Warning message 'Pilih salah satu template' appears; no API call made
status: pending
linked_change: 2026-06-11T13:15:57+07:00

[TEST]
id: T-026
timestamp: 2026-06-11T13:15:57+07:00
scope: storebuilder/app.js (handleGenerate + buildStoreData)
type: integration
description: After selecting template and clicking Generate, phase 4 shows iframe preview with generated site
inputs: Select 'Modern Agency', click 'Buat Website Sekarang'
expected: Phase 4 appears; iframe loads a complete store website HTML with product names from phase 2
status: pending
linked_change: 2026-06-11T13:15:57+07:00

[TEST]
id: T-027
timestamp: 2026-06-11T13:15:57+07:00
scope: storebuilder/index.html (approve button)
type: unit
description: Clicking the 'Konfirmasi & Lanjut' button in phase 2 also transitions to phase 3
inputs: Click 'Konfirmasi & Lanjut' button in phase 2
expected: Phase 3 skeleton chooser appears
status: pending
linked_change: 2026-06-11T13:15:57+07:00

[TEST]
id: T-028
timestamp: 2026-06-11T14:03:00+07:00
scope: storebuilder/index.html (phase 3)
type: unit
description: Exactly 3 skeleton template cards are shown in phase 3 representing Toko Klasik, Dashboard Modern, and Laporan Sederhana
inputs: Reach phase 3
expected: 3 cards visible in grid: Toko Klasik, Dashboard Modern, Laporan Sederhana
status: passing
linked_change: 2026-06-11T14:08:00+07:00

[TEST]
id: T-029
timestamp: 2026-06-11T14:03:00+07:00
scope: storebuilder/templates/toko-klasik.js
type: integration
description: Generating with Toko Klasik template produces a self-contained seller-only layout with blue/gray sidebar navigation and three pages
inputs: Select Toko Klasik template, click generate
expected: Iframe preview displays blue/gray sidebar layout containing exactly 3 tabs: Pesanan, Produk, Keuangan
status: passing
linked_change: 2026-06-11T14:08:00+07:00

[TEST]
id: T-030
timestamp: 2026-06-11T14:03:00+07:00
scope: storebuilder/templates/dashboard-modern.js
type: integration
description: Generating with Dashboard Modern template produces a self-contained seller-only dark layout with violet accents
inputs: Select Dashboard Modern template, click generate
expected: Iframe preview displays dark mode dashboard containing exactly 3 tabs: Pesanan, Produk, Keuangan
status: passing
linked_change: 2026-06-11T14:08:00+07:00

[TEST]
id: T-031
timestamp: 2026-06-11T14:03:00+07:00
scope: storebuilder/templates/laporan-sederhana.js
type: integration
description: Generating with Laporan Sederhana template produces a self-contained seller-only light minimalist layout with emerald accents
inputs: Select Laporan Sederhana template, click generate
expected: Iframe preview displays minimalist light layout containing exactly 3 tabs: Pesanan, Produk, Keuangan
status: passing
linked_change: 2026-06-11T14:08:00+07:00

[TEST]
id: T-032
timestamp: 2026-06-11T14:10:00+07:00
scope: storebuilder/app.js (handleGenerate + dbSaveSession)
type: regression
description: UI transition to phase 4 does not hang when database saving encounters a network latency or placeholder credential hang
inputs: Real Gemini key set, partial/invalid Firestore credentials, click generate
expected: Phase 4 loads preview successfully despite database connection state
status: passing
linked_change: 2026-06-11T14:11:00+07:00
