# Pizza Bench — privacy policy

The published privacy policy for the Pizza Bench iOS app. One static page, no build step.

Live at: `https://<your-github-username>.github.io/pizza-bench-privacy/`

---

## Publishing it (once)

**1. GitHub Desktop → `File → Add Local Repository…`** → choose this folder.
It will say there's no repository here — click **"create a repository"**.

- Name: `pizza-bench-privacy`
- Leave the git ignore and licence as None

**2. Click `Publish repository`.**
⚠️ **Uncheck "Keep this code private."** GitHub Pages needs a public repo on the free plan, and this page is meant to be public anyway.

**3. On github.com, open the repo → `Settings` → `Pages`:**

| Field | Value |
|---|---|
| Source | Deploy from a branch |
| Branch | `main` |
| Folder | `/ (root)` |

**Save.** The URL appears at the top of that page after about a minute. Open it and check it actually renders before going further.

**4. Paste the URL into App Store Connect → App Information → Privacy Policy URL.**

## Updating it later

Edit `index.html`, then in GitHub Desktop: write a summary → **Commit to main** → **Push origin**. Live within a minute.

**Change the date in two places** — the `<p class="updated">` near the top and the `<footer>` at the bottom.

---

## Two things that will bite if forgotten

**This URL must stay alive for as long as the app is in the store.** A dead privacy-policy link is a removal reason. Don't rename or delete the repo, and don't flip it to private.

**The policy must keep describing the code.** `app/../tests/privacy-surface.test.ts` fails whenever the app's data collection changes — a new event, a new network call, a new permission, a new SDK. When it fails, the order is:

1. Update `index.html` here, and push
2. Update the Privacy Nutrition Label in App Store Connect
3. Only then update the expected values in the test

The master copy of the text, plus the ready-made answers for Apple's Nutrition Label questionnaire, is in `02-standalone-path-ACTIVE/PRIVACY-POLICY.md`.

## Why plain HTML and not Jekyll

GitHub Pages will build a Jekyll site, but a Jekyll build can fail quietly on a bad theme or a stray character — and the result is a 404 where a privacy policy used to be. Static HTML cannot fail to build. The empty `.nojekyll` file tells Pages to skip the build entirely.
