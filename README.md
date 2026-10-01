# jingangchongapp-tools

Standalone HTML tools for **金刚宠 (Jingangchong Pet Grooming)**, 中山 / Zhongshan.

This repo hosts single-file HTML utilities that shop staff run in a browser.
They're separated from the main booking app (`wasahin/jiangangchong-app`) so:

- Tools deploy on their own cadence (no need to redeploy the booking app)
- File size growth from embedded assets (e.g. base64 logos) doesn't bloat the main repo
- Future tools land in the same place

## Current tools

### 1. Pet Health Tracking Card Generator (`pet-health-card.html`)

Staff tool — fills in pet weight/body dimensions/grooming notes on the left, renders a branded **毛孩子健康追踪卡** on the right, exports as 2× PNG to send customers via WeChat.

- **Zero deps** except html2canvas via CDN
- **Self-contained** — logo embedded as base64, no separate image needed
- **Brand v2** color palette applied (Sparkle Gold `#D4A24C` + Deep Navy `#1B3A5C`)
- **Single file** — open in any browser, works offline after first CDN fetch

#### How staff uses it

1. Open the URL (deployed via Cloudflare Pages)
2. Left: fill form (pet name, breed, weight, body dimensions, health checks, groomer)
3. Right: live-rendered branded card updates as you type
4. Click **📸 保存卡片图片** → downloads 2× resolution PNG
6. We forward PNG to customer in WeChat / 企业微信

If the save button doesn't respond (CDN unreachable), `Win+Shift+S` for screenshot fallback.

#### Local editing

Master source lives at `D:\金刚宠\jingangchong-app\Branding\pet_health_card_generator.html` (linked to this repo via deployment). To update:

1. Edit the local `Branding/` master
2. Sync to this repo's `pet-health-card.html` (logo base64 re-embedded if it changes)
3. Commit + push → Cloudflare Pages auto-rebuilds

## Deployment

Production URL: `https://xxx.space.mcode.cn/pet-health-card.html` (Cloudflare Pages — see Cloudflare dashboard for current URL)

GitHub Pages mirror (backup): `https://wasahin.github.io/jiangangchongapp-tools/pet-health-card.html`

## Adding a new tool

Drop a new `.html` file at repo root, add a row to the table above, commit + push. Cloudflare Pages rebuilds automatically.

## Source

Owned by **wasahin** on GitHub. Maintained by 道高 + Mavis agent (`jingangchong-analytics`).