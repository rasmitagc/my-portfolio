# Rasmita — Portfolio

A personal portfolio website — plain HTML, CSS, and JS, no build step, no framework.
Designed to be hosted free on **GitHub Pages** with a custom domain.

## Structure

```
Rasmita-Portfolio/
├── index.html        Home
├── about.html         About / background / skills
├── projects.html      Project showcase
├── poetry.html        Writing / poetry
├── hobbies.html        Hobbies
├── resume.html         Education, experience, resume download
├── contact.html         Contact form + links
├── css/style.css        All styles (design tokens at the top)
├── js/script.js          Mobile nav, footer year, scroll reveal
├── images/                Image assets
├── assets/                 Other files (e.g. resume.pdf)
├── favicon/                 favicon.ico goes here
├── CNAME                    Custom domain config for GitHub Pages
└── README.md
```

Every page shares the same header/nav and footer, copy-pasted at the top and bottom of each
file (no templating, since GitHub Pages serves static files only). If you add a new page,
copy the `<header>`/`<footer>` block from an existing one so the nav stays consistent.

## 1. Before you push: a few things to edit

- **Favicon** — add a real `favicon.ico` (or `.png`) into `/favicon`.
- **Resume** — add your PDF as `assets/resume.pdf` (the download button on `resume.html`
  expects this exact path).
- **Contact page** — replace the placeholder email, LinkedIn, and GitHub links in
  `contact.html`, and set up a free [Formspree](https://formspree.io) endpoint so the
  contact form actually sends you email (see the comment in that file).
- **Content** — swap the placeholder text in `about.html`, `projects.html`, `poetry.html`,
  `hobbies.html`, and `resume.html` for your own.

## 2. Create the GitHub repository

1. Go to [github.com/new](https://github.com/new).
2. Repository name: anything you like (e.g. `portfolio`) — it doesn't need to match your
   domain.
3. Keep it **Public** (required for free GitHub Pages).
4. Don't initialise with a README (you already have one) — leave it empty.
5. Click **Create repository**.

Then, from inside this folder on your computer:

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO.git
git push -u origin main
```

## 3. Turn on GitHub Pages

1. In your repo on GitHub, go to **Settings → Pages**.
2. Under **Build and deployment → Source**, choose **Deploy from a branch**.
3. Branch: `main`, folder: `/ (root)`. Click **Save**.
4. After a minute, GitHub will show your live URL:
   `https://YOUR-USERNAME.github.io/YOUR-REPO/`

Your site is now online — you can stop here if you don't need a custom domain yet.

## 4. Connect your custom domain

You said you already own a domain. Two DNS record types work, depending on whether you're
using the domain root (`example.com`) or a subdomain (`www.example.com`):

**Apex/root domain** (`example.com`) — add **A records** at your domain registrar pointing to
GitHub's IPs:
```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

**Subdomain** (`www.example.com`) — add a **CNAME record** instead, pointing to:
```
YOUR-USERNAME.github.io
```

Then:

1. Open the `CNAME` file in this repo and replace the placeholder with your actual domain,
   e.g. `www.example.com` or `example.com` (no `https://`, no trailing slash).
2. Commit and push that change.
3. In **Settings → Pages**, enter the same domain under **Custom domain** and save — GitHub
   will verify DNS automatically (this can take up to 24 hours, usually much less).
4. Once verified, tick **Enforce HTTPS**.

DNS changes can take anywhere from a few minutes to a few hours to propagate — if it doesn't
resolve immediately, that's normal.

## 5. Making future edits

- Edit any `.html` file directly for content changes.
- Edit `css/style.css` for styling — colours, fonts, and spacing are all defined as CSS
  variables at the top of the file (`:root { ... }`), so you can re-theme the whole site by
  changing a handful of values there.
- Edit `js/script.js` for behaviour (mobile menu, scroll effects).
- Commit and push — GitHub Pages redeploys automatically within a minute or two:

```bash
git add .
git commit -m "Update projects page"
git push
```

## Local preview

Open `index.html` directly in a browser, or serve it locally so relative paths behave
exactly as they will in production:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.
