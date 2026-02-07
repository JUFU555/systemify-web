# Automated Vercel Deployment

## How It Works

Every time code is pushed to the `main` branch, GitHub Actions automatically deploys to Vercel. No manual intervention needed.

## One-Time Setup (Already Completed)

### 1. GitHub Actions Workflow
✅ **Status:** Created at `.github/workflows/vercel-deploy.yml`

This workflow:
- Triggers on every push to `main`
- Installs Vercel CLI
- Builds the project
- Deploys to production

### 2. GitHub Secrets (REQUIRED - Must be added manually)

Go to GitHub repo → Settings → Secrets and variables → Actions → New repository secret

Add these three secrets:

**VERCEL_TOKEN**
- Get from: https://vercel.com/account/tokens
- Click "Create Token"
- Name it: "GitHub Actions - systemify-web"
- Scope: Full Account
- Copy the token and paste into GitHub secret

**VERCEL_ORG_ID**
- Value: `team_3jvAxYpkD86fMHFh4SajF318`
- (Found in `.vercel/project.json`)

**VERCEL_PROJECT_ID**
- Value: `prj_nZp8VS6y8ZCLZXydv0ttn3TYpOBB`
- (Found in `.vercel/project.json`)

## How to Deploy

### Automatic (Recommended)
```bash
git add .
git commit -m "Your commit message"
git push
```

That's it! GitHub Actions will handle the rest.

### Manual Trigger
1. Go to: https://github.com/JUFU555/systemify-web/actions
2. Click "Deploy to Vercel" workflow
3. Click "Run workflow"
4. Select `main` branch
5. Click "Run workflow"

## Monitoring Deployments

**GitHub Actions:**
https://github.com/JUFU555/systemify-web/actions

**Vercel Dashboard:**
https://vercel.com/julians-projects-6be49e0b/systemify-web

## Troubleshooting

### Deployment fails with "Unauthorized"
- Check that VERCEL_TOKEN is valid
- Regenerate token if needed: https://vercel.com/account/tokens

### Changes not showing up
- Check GitHub Actions tab for deployment status
- Deployment takes 1-2 minutes
- Hard refresh browser: Cmd+Shift+R (Mac) or Ctrl+Shift+R (Windows)

### Workflow not running
- Ensure `.github/workflows/vercel-deploy.yml` exists in repo
- Check that push was to `main` branch
- Verify GitHub Actions is enabled in repo settings

## Local Deployment (Backup Method)

If GitHub Actions is down or you need to deploy immediately:

```bash
cd /home/ubuntu/clawd/systemify-web
vercel --prod --yes
```

Note: Requires Vercel CLI authentication (`vercel login`)

---

**Last Updated:** 2026-02-07
**Project:** Systemify Web (systemify.vercel.app)
**Repo:** https://github.com/JUFU555/systemify-web
