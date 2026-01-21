# GitHub Pages Deployment Checklist

## Current Status
✅ Code pushed to `main` branch  
✅ GitHub Actions workflow configured (.github/workflows/deploy.yml)  
✅ 11ty site built and ready  

## Site URL
Your site should be available at: **https://terry81.github.io/prevodi-sema/**

## Steps to Enable GitHub Pages

### 1. Enable GitHub Pages (REQUIRED)

Go to your repository settings:
👉 **https://github.com/terry81/prevodi-sema/settings/pages**

You should see:

**Build and deployment:**
- **Source**: Select **"Deploy from a branch"**
- **Branch**: Select **"gh-pages"** and **"/ (root)"**
- Click Save

Note: We're using the gh-pages branch method (not GitHub Actions) to avoid environment protection issues.

### 2. Check GitHub Actions Status

Go to the Actions tab:
👉 **https://github.com/terry81/prevodi-sema/actions**

You should see:
- A workflow run called "Deploy to GitHub Pages"
- Status should be ✅ (green checkmark) or 🟡 (running)

If you see ❌ (red X), click on it to see the error.

### 3. Wait for Deployment

After pushing code, GitHub Actions will:
1. ⏳ Build the 11ty site (1-2 minutes)
2. ⏳ Deploy to GitHub Pages (30 seconds)
3. ✅ Site goes live!

Total time: ~2-3 minutes

### 4. Visit Your Site

Once deployment is complete:
- Visit: https://terry81.github.io/prevodi-sema/
- You should see the translation agency site with the dictionary banner

## Troubleshooting

### Site Shows 404 Not Found

**Check:**
1. Go to Settings > Pages
2. Verify "Source" is set to "GitHub Actions"
3. Check if the workflow completed successfully in Actions tab

**Fix:**
If workflow hasn't run, trigger it manually:
- Go to Actions tab
- Click "Deploy to GitHub Pages" workflow
- Click "Run workflow" button
- Select `main` branch
- Click green "Run workflow" button

### Workflow Failed

**Check the error:**
1. Go to Actions tab
2. Click on the failed workflow
3. Click on the failed job
4. Read the error message

**Common issues:**
- Missing dependencies: `npm ci` failed
  - Solution: Make sure package.json and package-lock.json are committed
- Build error: `npm run build` failed
  - Solution: Test build locally: `npm run build`
- Permission error: 
  - Solution: Go to Settings > Actions > General
  - Under "Workflow permissions", select "Read and write permissions"
  - Click Save

### Site Shows Old Content

**Clear your browser cache:**
- Mac: Cmd + Shift + R
- Windows: Ctrl + Shift + R
- Or open in incognito/private window

## Custom Domain (Optional)

If you want to use **prevodi-sema.com** instead of GitHub Pages URL:

1. Add CNAME file:
   ```bash
   echo "prevodi-sema.com" > src/CNAME
   git add src/CNAME
   git commit -m "Add custom domain"
   git push
   ```

2. Update .eleventy.js to copy CNAME:
   ```javascript
   eleventyConfig.addPassthroughCopy("src/CNAME");
   ```

3. Configure DNS at your domain registrar:
   - Add CNAME record: `www` → `terry81.github.io`
   - Add A records for apex domain:
     - 185.199.108.153
     - 185.199.109.153
     - 185.199.110.153
     - 185.199.111.153

4. In GitHub Settings > Pages:
   - Enter `prevodi-sema.com` in Custom domain field
   - Wait for DNS check to complete
   - Enable "Enforce HTTPS"

## Quick Verification Commands

Run these locally to verify everything:

```bash
# Check you're on main branch
git branch

# Check remote is set
git remote -v

# Test build locally
npm run build

# Check if _site folder was created
ls -la _site/
```

## Next Steps After Site is Live

1. ✅ Verify all 7 pages load correctly
2. ✅ Test navigation menu and dropdown
3. ✅ Check banner image displays properly
4. ✅ Test on mobile devices
5. ✅ Check Google Maps on Contacts page
6. ✅ Test all links work

## Summary

**What you need to do RIGHT NOW:**

1. Go to https://github.com/terry81/prevodi-sema/settings/pages
2. Set Source to "GitHub Actions"
3. Go to https://github.com/terry81/prevodi-sema/actions
4. Wait for workflow to complete (~2 minutes)
5. Visit https://terry81.github.io/prevodi-sema/

That's it! Your site should be live! 🚀

---

**Need help?** Check the Actions tab for detailed logs if something goes wrong.
