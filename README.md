# GENX CHOICE ENTERPRISE — WhatsApp Shop

Customers browse products, add to cart, then tap "Order on WhatsApp" —
it opens WhatsApp with the order already typed out. No payment gateway,
no monthly hosting cost.

Built to scale to a large catalogue: product photos are stored as their
own small files (not crammed into one giant file), and the shop only
renders products in batches as customers scroll — so it stays fast even
with hundreds or thousands of products.

## Files
- **index.html** — the shop customers see
- **admin.html** — the page *you* use to add categories, products and photos
- **products.json** — where your catalogue's text data lives
- **logo.png** — your logo

## Step 1 — Put it on GitHub Pages (one-time)

1. Create a free account at [github.com](https://github.com) if needed.
2. **New repository** → name it (e.g. `store`) → set **Public** → **Create repository**.
3. **Add file → Upload files** → drag in `index.html`, `admin.html`,
   `products.json`, `logo.png` → commit.
4. **Settings → Pages** → Source: `Deploy from a branch`, branch `main`,
   folder `/root` → Save.
5. Wait ~1 minute, refresh — your live link appears, e.g.
   `https://yourusername.github.io/store/`.

## Step 2 — Connect Shop Manager to GitHub (one-time)

This lets `admin.html` publish updates straight to your live site — no
downloading or pasting files by hand.

1. On GitHub, tap your profile photo → **Settings** → scroll down to
   **Developer settings** (bottom of the left sidebar) → **Personal access
   tokens** → **Fine-grained tokens** → **Generate new token**.
2. Give it a name (e.g. "Shop Manager"), leave the expiry as-is or extend it.
3. Under **Repository access**, choose **Only select repositories** and
   pick your shop's repo (e.g. `store`).
4. Under **Permissions → Repository permissions**, find **Contents** and
   set it to **Read and write**. Leave everything else as **No access**.
5. Click **Generate token**, then **copy it immediately** — GitHub only
   shows it once. Treat it like a password; don't share it.
6. Open `https://yourusername.github.io/store/admin.html` on your live
   site. Tap **GitHub connection settings** to expand it, and fill in:
   - **GitHub username** — your GitHub username
   - **Repository name** — e.g. `store`
   - **Branch** — `main`
   - **Folder** — leave blank if your files sit at the repo's root
     (as in Step 1); only fill this in if you placed them in a subfolder
   - **Personal access token** — paste the token you just copied
7. Tap **Save settings**, then **Test connection** — it should show
   *"Connected to yourusername/store ✓"* with a green dot.

That's it — this only needs doing once per device/browser.

## Step 3 — Add categories and products

1. **Add categories first** — type a name like "Chargers", tap Add category.
2. **Add products** — name, price, category, stock status, and tap the
   photo box to upload a picture from your phone or computer.
3. Once you've added what you need, tap **🚀 Publish to live site**.
   You'll see a live log as it uploads each photo and saves your
   catalogue — when it says *"Publish complete"*, refresh your shop link
   and your products are there.
4. Products show a **LIVE** or **PENDING** tag in the list — PENDING
   means it hasn't been published yet (e.g. you just changed its stock
   status). Publish again to push the update.

Repeat step 3 anytime — add, edit stock, delete, then Publish.

### No token? Use Manual mode instead

Tap **📥 Manual** at the top of Shop Manager to switch back to the
download/upload workflow: build your catalogue, click **Download
products.json**, then replace the file in your GitHub repo yourself.
Works without a token, just more steps each time.

## Editing the WhatsApp number

Open `index.html`, find near the top of the `<script>` section:

```js
const WHATSAPP_NUMBER = "233549572669"; // international format, no + or spaces
```

Set to your number `0549572669` in international format (Ghana's `233`
replacing the leading `0`). Change here and re-publish if it ever changes.

## How big can the catalogue get?

- Each photo is auto-compressed to roughly 40–80KB and stored as its own
  file under an `images/` folder — so `products.json` itself stays small
  (a few hundred KB) even with thousands of products.
- The storefront shows 24 products at a time with a **"Show more"**
  button, so browsing stays fast no matter how large the catalogue gets.
- Comfortably handles a catalogue in the thousands of products.

## Notes
- Your GitHub token is stored only in the browser you set it up in
  (never sent anywhere except to GitHub). If you manage the shop from a
  new device, you'll need to paste the token in again there.
- If a category is deleted while products still use it, Shop Manager
  warns you first.
- The site is mobile-first, since that's how most customers arrive from
  a shared WhatsApp/Instagram link.
