# রাফখাতা — Complete Setup Guide
## Hugo + PaperMod + Decap CMS → GitHub Pages → mhlimon.com

**Time required**: ~40 minutes  
**Result**: Professional personal site, live at mhlimon.com, with web admin panel

---

## What You Get

| Feature | Detail |
|---|---|
| Hosting | GitHub Pages (free) |
| CMS / Admin | Decap CMS at `/admin` — write posts in a web UI |
| Bangla posts | Stored as `.md` files in GitHub forever |
| Tech blog | Full search, tags, reading time |
| Arabic section | Lessons + vocab |
| Dark/Light toggle | Built into PaperMod |
| Comments | Giscus (GitHub Discussions) |
| SEO | Auto sitemap, RSS, Open Graph |
| Custom domain | mhlimon.com (your own) |

---

## STEP 1 — Create GitHub Repository

1. Go to [github.com/new](https://github.com/new)
2. Repository name: **`mhlimon`**
3. Visibility: **Public** (required for free GitHub Pages)
4. **Do NOT** check "Add a README file"
5. Click **Create repository**
6. Note your GitHub username — you'll need it in step 3

---

## STEP 2 — Upload All Files

You received a ZIP file containing the complete site. Upload it to GitHub:

**Option A (easy): GitHub web editor**
1. In your new repo, click **"uploading an existing file"**
2. Drag and drop all files from the ZIP
3. Commit: "Initial site setup"

**Option B (Git CLI)**
```bash
git clone https://github.com/YOUR_USERNAME/mhlimon.git
# Copy all files into the cloned folder
cd mhlimon
git add .
git commit -m "Initial site setup"
git push origin main
```

### Add PaperMod theme (CRITICAL step)

After uploading, add the theme as a submodule. In your repo:

1. Go to your repo → **Code** tab
2. Click the **"..."** (three dots) → **"Open with GitHub Desktop"**

OR via Git CLI:
```bash
cd mhlimon
git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
git add .gitmodules themes/
git commit -m "Add PaperMod theme"
git push
```

OR: if you don't have Git CLI, in your repo create the file `.gitmodules` with the content already provided — GitHub's Actions workflow will handle the submodule on build.

---

## STEP 3 — Replace YOUR_GITHUB_USERNAME

Open these files and replace `YOUR_GITHUB_USERNAME` with your actual GitHub username:

1. **`hugo.toml`** → line with `editPost.URL`
2. **`static/admin/config.yml`** → line with `repo:`
3. **`layouts/partials/comments.html`** → line with `data-repo=`

You can do this in the GitHub web editor (click the file → pencil icon).

---

## STEP 4 — Enable GitHub Pages

1. In your repo → **Settings** → **Pages** (left sidebar)
2. Under "Source" → **GitHub Actions** (not "Deploy from a branch")
3. That's it — the workflow file already handles everything

GitHub will start building. Check progress under **Actions** tab.

---

## STEP 5 — Point Your Domain

In your domain registrar (where mhlimon.com is registered):

Add these DNS A records:
```
Type: A   Name: @   Value: 185.199.108.153
Type: A   Name: @   Value: 185.199.109.153
Type: A   Name: @   Value: 185.199.110.153
Type: A   Name: @   Value: 185.199.111.153
Type: CNAME  Name: www  Value: YOUR_USERNAME.github.io
```

Back in GitHub Pages settings:
- Custom domain: `mhlimon.com`
- Check ✅ **Enforce HTTPS**

DNS takes 10–60 minutes to propagate.

---

## STEP 6 — Enable Decap CMS Admin

The `/admin` panel uses GitHub for login.

1. Go to [github.com/settings/developers](https://github.com/settings/developers)
2. **OAuth Apps** → **New OAuth App**
3. Fill in:
   - Application name: `mhlimon CMS`
   - Homepage URL: `https://mhlimon.com`
   - Authorization callback URL: `https://api.netlify.com/auth/done`
4. Note the **Client ID** and generate a **Client Secret**

Then (simplest option) deploy a small Netlify site for OAuth:
1. Go to [netlify.com](https://netlify.com) → new site from template
2. Deploy this repo: `vencax/netlify-cms-github-oauth-provider`
3. Set env vars: `OAUTH_CLIENT_ID` and `OAUTH_CLIENT_SECRET`
4. In `static/admin/config.yml` add:
   ```yaml
   backend:
     base_url: https://YOUR_NETLIFY_OAUTH_APP.netlify.app
   ```

**Simpler alternative**: Use Netlify to host the whole site (instead of GitHub Pages). Netlify has built-in OAuth for Decap CMS with zero extra setup. Just:
1. netlify.com → Import from GitHub → your `mhlimon` repo
2. Build command: `hugo`, Publish: `public`
3. Add custom domain `mhlimon.com`
4. Done — `/admin` works immediately

---

## STEP 7 — Set Up Giscus Comments

1. Go to [giscus.app](https://giscus.app)
2. Enter your repo: `YOUR_USERNAME/mhlimon`
3. Enable Discussions on your repo (Settings → Features → Discussions ✅)
4. Choose "pathname" mapping
5. Copy the generated script values
6. Paste into `layouts/partials/comments.html`:
   - `data-repo-id`
   - `data-category-id`

---

## Daily Workflow (After Setup)

### Write a new Bangla post:
1. Go to `mhlimon.com/admin`
2. Login with GitHub
3. Click **📖 বাংলা সাহিত্য** → **New বাংলা পোস্ট**
4. Fill title, date, tags, body (rich text editor)
5. Click **Publish** → site rebuilds in ~60 seconds

### Add a daily note:
1. Admin → **📝 Daily Notes** → New Note
2. One-liner title → Publish
3. Appears in homepage sidebar automatically

### Add a tech post:
1. Admin → **💻 Tech Blog** → New Post
2. Write in Markdown → Publish

### Add a video:
1. Get the YouTube video ID (e.g. `dQw4w9WgXcQ` from `youtube.com/watch?v=dQw4w9WgXcQ`)
2. Admin → **▶ Videos** → New Video
3. Paste the ID in "YouTube Video ID" field → Publish

---

## File Structure Reference

```
mhlimon/
├── .github/workflows/hugo.yml   ← Auto-deploy on every push
├── content/
│   ├── bangla/                  ← Your Bangla posts (Markdown)
│   ├── tech/                    ← Tech blog posts
│   ├── notes/                   ← Daily notes (sidebar)
│   ├── arabic/                  ← Arabic lessons
│   ├── projects/                ← Project cards
│   ├── videos/                  ← YouTube video entries
│   ├── cv.md                    ← Your CV page
│   └── search.md                ← Search page
├── layouts/
│   ├── index.html               ← Custom homepage
│   ├── _default/single.html     ← Single post layout
│   ├── partials/comments.html   ← Giscus comments
│   └── shortcodes/rawhtml.html  ← Raw HTML shortcode
├── assets/css/extended/
│   └── custom.css               ← All custom styling
├── static/admin/
│   ├── config.yml               ← Decap CMS config
│   └── index.html               ← Admin panel HTML
├── hugo.toml                    ← Site config
└── .gitmodules                  ← PaperMod theme reference
```

---

## Costs

| Service | Cost |
|---|---|
| GitHub (hosting + content) | Free |
| GitHub Pages (serving) | Free |
| Decap CMS | Free |
| Giscus comments | Free |
| mhlimon.com domain | Already have it |
| **Total** | **$0/month** |

---

## Troubleshooting

**Site not building?**
- Check Actions tab in GitHub → look for errors
- Most common: `.gitmodules` missing or theme not loaded

**Admin (/admin) not working?**
- OAuth not set up — use Netlify hosting for easiest fix
- Or add `base_url` to `static/admin/config.yml`

**Custom domain not loading?**
- DNS propagation takes up to 24h
- Check `Settings → Pages` in GitHub — should show "Your site is live at mhlimon.com"

**Posts not showing on homepage?**
- Check `draft: false` in the post's front matter
- Check section matches (`bangla`, `tech`, `notes`)

---

Reply here with "deployed" or paste any error message — I'll debug it immediately.
