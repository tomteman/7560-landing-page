# Migration Guide: Vercel to GitHub Pages

This guide will help you migrate your RIP-7560 landing page from Vercel to GitHub Pages and set up Cloudflare DNS.

## What's Been Done

1. ✅ Created a static HTML version of your Next.js landing page (`index.html`)
2. ✅ Moved assets to the `assets/` directory for GitHub Pages compatibility
3. ✅ Created GitHub Actions workflow for automatic deployment
4. ✅ Preserved all styling and functionality using Tailwind CSS CDN

## Step 1: Enable GitHub Pages

1. Go to your GitHub repository
2. Navigate to **Settings** → **Pages**
3. Under **Source**, select **GitHub Actions**
4. This will use the workflow we created in `.github/workflows/deploy.yml`

## Step 2: Push Changes to GitHub

```bash
git add .
git commit -m "Migrate to GitHub Pages: Add static HTML and GitHub Actions workflow"
git push origin main
```

## Step 3: Set Up Custom Domain (Optional)

If you want to use a custom domain instead of `username.github.io/repo-name`:

1. In your repository's **Settings** → **Pages**
2. Under **Custom domain**, enter your domain (e.g., `rip7560.com`)
3. Check **Enforce HTTPS**
4. Save the changes

## Step 4: Cloudflare DNS Configuration

### If using a custom domain:

1. **Add your domain to Cloudflare** (if not already done)
2. **Create DNS records** in Cloudflare:

   **Option A: Using CNAME (Recommended)**
   ```
   Type: CNAME
   Name: @ (or your subdomain)
   Target: username.github.io
   Proxy status: Proxied (orange cloud)
   ```

   **Option B: Using A records**
   ```
   Type: A
   Name: @
   Target: 185.199.108.153
   Proxy status: Proxied (orange cloud)
   ```
   
   ```
   Type: A
   Name: @
   Target: 185.199.109.153
   Proxy status: Proxied (orange cloud)
   ```
   
   ```
   Type: A
   Name: @
   Target: 185.199.110.153
   Proxy status: Proxied (orange cloud)
   ```
   
   ```
   Type: A
   Name: @
   Target: 185.199.111.153
   Proxy status: Proxied (orange cloud)
   ```

3. **Create a CNAME file** in your repository root:
   ```
   yourdomain.com
   ```

### If using GitHub Pages default URL:
No additional DNS configuration needed. Your site will be available at:
`https://username.github.io/repo-name`

## Step 5: Verify Deployment

1. Wait for the GitHub Actions workflow to complete (check the **Actions** tab)
2. Visit your site at the GitHub Pages URL or your custom domain
3. Test all links and functionality

## Step 6: Update Vercel (Cleanup)

1. Go to your Vercel dashboard
2. Find this project
3. Go to **Settings** → **General**
4. Scroll down and click **Delete Project**
5. Confirm deletion

## File Structure After Migration

```
7560-landing-page/
├── index.html              # Static HTML version of your landing page
├── assets/                 # Images and other static assets
│   ├── ERC-4337-team-logo-color.svg
│   └── ERC-4337-team-logo-color-light.svg
├── .github/workflows/      # GitHub Actions deployment workflow
│   └── deploy.yml
├── MIGRATION_GUIDE.md      # This file
└── [other Next.js files]   # Can be removed after migration
```

## Benefits of This Migration

- ✅ **Free hosting** on GitHub Pages
- ✅ **Automatic deployments** via GitHub Actions
- ✅ **CDN and HTTPS** included
- ✅ **Custom domain support** with Cloudflare
- ✅ **Same visual design** and functionality
- ✅ **Dark mode support** preserved
- ✅ **Mobile responsive** design maintained

## Troubleshooting

### If images don't load:
- Check that the `assets/` directory contains the SVG files
- Verify the paths in `index.html` are correct

### If GitHub Pages doesn't deploy:
- Check the **Actions** tab for any error messages
- Ensure the workflow file is in the correct location: `.github/workflows/deploy.yml`

### If custom domain doesn't work:
- Verify DNS records are correctly configured in Cloudflare
- Check that the CNAME file in your repository matches your domain
- Wait up to 24 hours for DNS propagation

## Next Steps

After successful migration, you can optionally:

1. **Remove Next.js files** (optional, for cleanup):
   ```bash
   rm -rf app/ .next/ next.config.mjs package.json package-lock.json
   rm -rf node_modules/ tailwind.config.ts postcss.config.mjs
   rm -rf tsconfig.json .eslintrc.json next-env.d.ts
   ```

2. **Update repository description** to reflect the new hosting

3. **Test thoroughly** to ensure everything works as expected

Your landing page will now be hosted for free on GitHub Pages with automatic deployments on every push to the main branch! 