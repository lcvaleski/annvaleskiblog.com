# Cloudflare Pages Deployment Guide for annvaleskiblog.com

## Project Structure
This is a static website with no build process required. The files are served directly.

## Cloudflare Pages Setup

### Step 1: Connect to Git Repository
1. Go to [Cloudflare Dashboard](https://dash.cloudflare.com)
2. Navigate to "Workers & Pages" > "Create application" > "Pages"
3. Connect to Git (GitHub/GitLab)
4. Select your repository

### Step 2: Configure Build Settings
Use these settings when setting up the project:

- **Project name**: `annvaleskiblog`
- **Production branch**: `main`
- **Build command**: (leave empty - no build needed)
- **Build output directory**: `/`
- **Root directory**: `/` (or leave empty)

### Step 3: Environment Variables
No environment variables needed for the static site.

The CMS admin panel (in `/cms-admin`) would need separate deployment if you want to use it.

### Step 4: Custom Domain Setup
1. After deployment, go to your Pages project settings
2. Click on "Custom domains" tab
3. Add `annvaleskiblog.com`
4. Follow the DNS configuration instructions:
   - Either use Cloudflare DNS (recommended)
   - Or add a CNAME record pointing to your `.pages.dev` subdomain

### Step 5: DNS Configuration (if using Cloudflare DNS)
Cloudflare will automatically configure the DNS records when you add the custom domain.

If managing DNS elsewhere, add:
```
CNAME @ your-project.pages.dev
CNAME www your-project.pages.dev
```

## Files Being Deployed
- `index.html` - Main blog page
- `header.png` - Header image
- `CNAME` - GitHub Pages file (can be removed for Cloudflare)

## Post-Deployment Steps
1. Verify the site is accessible at `https://annvaleskiblog.com`
2. Check SSL certificate is active (automatic with Cloudflare)
3. Test the newsletter subscription form
4. Update the CMS API URL if deploying the admin panel separately

## Notes
- The CNAME file is for GitHub Pages and can be deleted when using Cloudflare Pages
- The `/cms-admin` folder contains a Next.js app that would need separate deployment on Vercel or another platform
- Static assets (images, etc.) are served directly from the repository