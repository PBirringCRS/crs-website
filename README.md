# Copper Ridge Security Website

Professional static website for Copper Ridge Security LLC - Federal cybersecurity contractor specializing in RMF/ATO, CMMC, and compliance services.

## 📁 File Structure

```
copper-ridge-website/
├── index.html                          # Home page
├── about/
│   └── index.html                     # About page
├── services/
│   └── index.html                     # Services page
├── past-performance/
│   └── index.html                     # Past performance page
├── contact/
│   └── index.html                     # Contact page
└── assets/
    ├── styles.css                     # Main stylesheet
    └── Capability-Statement.pdf       # Upload your PDF here
```

## 🚀 Deployment to Azure Static Web Apps

### Prerequisites
- GitHub account
- Azure subscription
- Azure CLI (optional, can use Azure Portal)

### Step 1: Create GitHub Repository

1. Create a new repository on GitHub (e.g., `copper-ridge-security-website`)
2. Upload all website files to the repository maintaining the folder structure above

### Step 2: Deploy to Azure Static Web Apps

#### Option A: Using Azure Portal (Easiest)

1. Go to [Azure Portal](https://portal.azure.com)
2. Click "Create a resource" → Search for "Static Web Apps"
3. Click "Create"
4. Fill in the details:
   - **Subscription**: Select your Azure subscription
   - **Resource Group**: Create new or select existing
   - **Name**: `copper-ridge-security` (or your preferred name)
   - **Plan type**: Select "Free" for development or "Standard" for production
   - **Region**: Choose closest to your target audience
   - **Source**: Select "GitHub"
5. Authorize GitHub and select:
   - **Organization**: Your GitHub username/org
   - **Repository**: Your repository name
   - **Branch**: `main` or `master`
6. Build Details:
   - **Build Presets**: Select "Custom"
   - **App location**: `/` (root directory)
   - **Api location**: Leave blank
   - **Output location**: Leave blank
7. Click "Review + create" → "Create"

#### Option B: Using Azure CLI

```bash
# Login to Azure
az login

# Create resource group
az group create --name copper-ridge-rg --location eastus

# Create static web app (replace with your GitHub details)
az staticwebapp create \
  --name copper-ridge-security \
  --resource-group copper-ridge-rg \
  --source https://github.com/YOUR-USERNAME/YOUR-REPO \
  --location eastus \
  --branch main \
  --app-location "/" \
  --login-with-github
```

### Step 3: Upload Capability Statement PDF

1. After deployment, go to your repository
2. Navigate to `assets/` folder
3. Upload your `Capability-Statement.pdf` file
4. Commit the change
5. Azure will automatically redeploy with the PDF

### Step 4: Configure Custom Domain (Optional)

1. In Azure Portal, go to your Static Web App
2. Click "Custom domains" in the left menu
3. Click "Add"
4. Enter your custom domain (e.g., `www.copperridgesecurity.com`)
5. Follow instructions to add DNS records with your domain provider
6. Wait for DNS propagation (can take up to 48 hours)

## 📝 Customization Guide

### Adding Microsoft Forms Contact Form

1. Go to [forms.microsoft.com](https://forms.office.com)
2. Create a new form with your desired fields
3. Click "Share" → "Embed"
4. Copy the iframe embed code
5. Open `contact/index.html`
6. Find the comment section that says "PASTE YOUR MICROSOFT FORMS EMBED CODE HERE"
7. Replace the placeholder div with your iframe code
8. Commit and push changes

Example iframe format:
```html
<iframe 
    width="100%" 
    height="600px" 
    src="https://forms.office.com/Pages/ResponsePage.aspx?id=YOUR_FORM_ID" 
    frameborder="0" 
    style="border: none; max-width:100%; max-height:100vh" 
    allowfullscreen>
</iframe>
```

### Updating Business Information

Update the following placeholders once you receive them:

1. **UEI Number**: Search for "Pending SAM.gov registration" and replace with actual UEI
2. **CAGE Code**: Search for "Pending SAM.gov registration" and replace with actual CAGE
3. Add any additional NAICS codes or certifications as needed

### Adding Logo Images

The site currently uses text-based branding. To add your logo:

1. Upload logo images to `assets/` folder:
   - `logo-primary.png` (for header)
   - `logo-footer.png` (for footer, if different)
2. Update the header logo in each HTML file:

Replace:
```html
<a href="/" class="site-logo">
    <span>COPPER RIDGE SECURITY</span>
</a>
```

With:
```html
<a href="/" class="site-logo">
    <img src="/assets/logo-primary.png" alt="Copper Ridge Security" height="40">
</a>
```

### Customizing Colors

The brand colors are defined in `assets/styles.css` at the top:

```css
:root {
    --navy-primary: #1E3A52;
    --copper-accent: #C28C70;
    /* Modify these values to change the color scheme */
}
```

## 🔒 Security Considerations

- No JavaScript required (reduces attack surface)
- All forms handled via Microsoft Forms (no backend needed)
- Static files only (no server-side processing)
- HTTPS automatically enabled via Azure Static Web Apps
- Content Security Policy can be added via `staticwebapp.config.json`

## 📱 Responsive Design

The site is fully responsive and tested on:
- Desktop (1920px+)
- Laptop (1024px - 1919px)
- Tablet (768px - 1023px)
- Mobile (320px - 767px)

## ♿ Accessibility Features

- Semantic HTML structure
- Proper heading hierarchy (h1 → h6)
- Skip to main content link
- High contrast text (WCAG AA compliant)
- Focus visible states on all interactive elements
- Alt text placeholders for images
- Keyboard navigation support

## 📊 Analytics (Optional)

To add Google Analytics or other tracking:

1. Get your tracking code
2. Add to the `<head>` section of each HTML file before closing `</head>` tag
3. Commit and redeploy

## 🆘 Support

For questions about deployment or customization:
- Azure Static Web Apps docs: https://docs.microsoft.com/azure/static-web-apps/
- GitHub Pages alternative: https://pages.github.com/

## 📄 License

© 2026 Copper Ridge Security LLC. All rights reserved.

---

## Quick Deploy Checklist

- [ ] Create GitHub repository
- [ ] Upload all website files
- [ ] Create Azure Static Web App
- [ ] Connect to GitHub repository
- [ ] Upload Capability Statement PDF
- [ ] Configure Microsoft Forms (optional)
- [ ] Update UEI/CAGE when available
- [ ] Test on mobile and desktop
- [ ] Configure custom domain (optional)
- [ ] Add analytics tracking (optional)
