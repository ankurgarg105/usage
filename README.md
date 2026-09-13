# Card Rewards Finder

Minimal static web app for checking which card rule applies to a transaction.

## Files
- `index.html` — app UI and matching logic
- `data/card_rewards_rules.json` — 172 supplied card rules
- `.github/workflows/deploy.yml` — GitHub Pages deployment + daily scheduled refresh

## GitHub Pages setup
1. Create a new **public** GitHub repository.
2. Upload all files from this folder, preserving `.github/workflows/deploy.yml`.
3. Go to **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to **GitHub Actions**.
5. Open **Actions** and run **Deploy to GitHub Pages** once manually if needed.
6. Your site will be available at `https://YOUR_USERNAME.github.io/REPOSITORY_NAME/`.

## Daily refresh
The workflow runs daily and deploys the current repository contents. It does not invent or alter card rules. Update `data/card_rewards_rules.json` whenever the bank/card terms change.

## Important data note
Amazon, Flipkart and Myntra are represented as merchant identifiers rather than numeric MCCs because those entries in the supplied source data were merchant names. Non-MCC PhonePe rules have `mcc: null`.

## Recommendation logic
The app matches category first, then optional MCC/merchant/mode constraints. It shows the stated reward rate and calculates the benefit for percentage cashback or RP-per-₹100 rules when an amount is supplied. It does **not** assign a rupee value to reward points.
