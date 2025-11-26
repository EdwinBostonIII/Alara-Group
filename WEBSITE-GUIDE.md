# Alara Group Website Guide

This guide provides everything you need to maintain, edit, and deploy the Alara Group website.

## Table of Contents

1. [Quick Start](#quick-start)
2. [File Structure](#file-structure)
3. [Editing Content](#editing-content)
4. [Design System](#design-system)
5. [Adding New Pages](#adding-new-pages)
6. [Contact Form Setup](#contact-form-setup)
7. [Deployment](#deployment)
8. [Troubleshooting](#troubleshooting)

---

## Quick Start

### Preview Locally

To preview the website on your computer:

1. Open a terminal in the project folder
2. Run one of these commands:

```powershell
# Using npx (requires Node.js)
npx serve .

# Or use Python's built-in server
python -m http.server 8000
```

3. Open your browser to `http://localhost:5000` (or `http://localhost:8000` for Python)

### Deploy Changes

The site is hosted on Cloudflare Pages. To deploy:

1. Make your changes
2. Commit to Git: `git add . && git commit -m "Your message"`
3. Push to GitHub: `git push`
4. Cloudflare Pages will automatically deploy within a few minutes

---

## File Structure

```
Alara-Group/
├── index.html          # Homepage
├── about.html          # About Us page
├── services.html       # Services page
├── markets.html        # Markets/Industries page
├── blog.html           # Insights/Blog page
├── contact.html        # Contact page with form
├── css/
│   └── styles.css      # Custom styles (minimal)
├── WEBSITE-GUIDE.md    # This file
└── README.md           # Project readme
```

---

## Editing Content

### Text Content

All text is directly in the HTML files. To edit:

1. Open the relevant `.html` file
2. Find the text you want to change
3. Edit it directly
4. Save the file

**Important:** Avoid using em-dashes (—) or in-text hyphens. Use commas or restructure sentences instead.

### Images

Currently the site uses SVG icons and gradient placeholders. To add images:

1. Create an `images/` folder
2. Add your images (use `.jpg`, `.png`, or `.webp` formats)
3. Reference them in HTML:

```html
<img src="images/your-image.jpg" alt="Description of image" class="rounded-2xl">
```

### Social Links

Social media links are in the footer of every page. To update:

1. Find this section in each HTML file:
```html
<a href="https://www.linkedin.com/company/alara-group-ltd" ...
```
2. Update the URLs as needed

Current social profiles:
- LinkedIn: `https://www.linkedin.com/company/alara-group-ltd`
- Facebook: `https://www.facebook.com/alaragroupltd`
- X/Twitter: `https://www.x.com/alaragroupltd`

---

## Design System

### Colors

The site uses a custom color palette defined in the Tailwind config:

| Color | Usage |
|-------|-------|
| `navy-50` to `navy-950` | Primary brand colors (backgrounds, text) |
| `gold-50` to `gold-900` | Accent colors (buttons, highlights) |
| `warm-50` to `warm-200` | Neutral backgrounds |

### Typography

- **Headings**: `font-heading` (Inter font)
- **Body text**: `font-body` (Open Sans font)

### Common UI Patterns

**Buttons (Primary CTA):**
```html
<a href="contact.html" class="bg-gradient-to-r from-gold-500 to-gold-600 text-white px-8 py-4 rounded-full font-heading font-semibold text-lg hover:from-gold-600 hover:to-gold-700 transition-all shadow-lg shadow-gold-500/25">
    Button Text
</a>
```

**Cards:**
```html
<div class="bg-white rounded-2xl p-8 shadow-lg border border-navy-100">
    <!-- Card content -->
</div>
```

**Section Spacing:**
- Use `py-24` for major sections
- Use `max-w-7xl mx-auto px-4 sm:px-6 lg:px-8` for content containers

---

## Adding New Pages

1. Copy an existing page (like `about.html`) as a template
2. Rename it (e.g., `new-page.html`)
3. Update the navigation in the new page:
   - Change the active link to have class `text-gold-600 border-b-2 border-gold-500 font-medium pb-1`
   - Other nav links should have `text-navy-600 hover:text-gold-600 transition-colors`
4. Update the page content
5. Add the page to navigation in ALL other pages

### Navigation Example

Active page:
```html
<a href="new-page.html" class="text-gold-600 border-b-2 border-gold-500 font-medium pb-1">New Page</a>
```

Other pages:
```html
<a href="new-page.html" class="text-navy-600 hover:text-gold-600 transition-colors">New Page</a>
```

---

## Contact Form Setup

The contact form uses [Formspree](https://formspree.io/) to handle submissions.

### Setting Up Formspree

1. Go to [formspree.io](https://formspree.io/) and create an account
2. Create a new form
3. Copy your form ID (looks like `f/xyzabc123`)
4. In `contact.html`, find this line:
```html
<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
```
5. Replace `YOUR_FORM_ID` with your actual form ID

### Form Notifications

In your Formspree dashboard, you can:
- Set up email notifications
- Configure spam protection
- View submission history
- Export submissions

---

## Deployment

### Cloudflare Pages Setup (First Time)

1. Go to [Cloudflare Pages](https://pages.cloudflare.com/)
2. Sign in with your Cloudflare account
3. Click "Create a project"
4. Connect your GitHub account
5. Select the `Alara-Group` repository
6. Configure build settings:
   - Framework preset: None
   - Build command: (leave empty)
   - Build output directory: `/`
7. Click "Save and Deploy"

### Custom Domain

To use a custom domain:

1. In Cloudflare Pages, go to your project
2. Click "Custom domains"
3. Add your domain (e.g., `alaragroupltd.com`)
4. Follow the DNS configuration instructions

### Automatic Deployments

Every push to the `main` branch will automatically trigger a new deployment. You can view deployment status in the Cloudflare Pages dashboard.

---

## Troubleshooting

### Changes Not Showing

1. **Clear browser cache**: Press `Ctrl+Shift+R` (Windows) or `Cmd+Shift+R` (Mac)
2. **Wait for deployment**: Cloudflare deployments take 1-3 minutes
3. **Check deployment status**: View the Cloudflare Pages dashboard

### Styling Issues

If styles look broken:
1. Check that the Tailwind CDN link is present in the `<head>`:
```html
<script src="https://cdn.tailwindcss.com"></script>
```
2. Verify the Tailwind config is included after the CDN script

### Mobile Menu Not Working

The mobile menu requires JavaScript. Check that this script is at the bottom of your HTML:
```html
<script>
    const mobileMenuBtn = document.getElementById('mobile-menu-btn');
    const mobileMenu = document.getElementById('mobile-menu');
    
    mobileMenuBtn.addEventListener('click', () => {
        mobileMenu.classList.toggle('hidden');
    });
</script>
```

### Form Not Submitting

1. Verify your Formspree form ID is correct
2. Check that the form `action` URL is correct
3. Ensure all required fields have the `required` attribute

---

## Support

For technical support or questions about the website, contact:
- Email: info@alaragroupltd.com

---

## Quick Reference

### Key URLs
- **GitHub Repository**: Your repository URL
- **Live Site**: Your Cloudflare Pages URL
- **Formspree Dashboard**: https://formspree.io/forms

### Brand Information
- **Company Name**: Alara Group Ltd
- **Founders**: Cindy G. Levitt, David Levitt
- **Primary Email**: info@alaragroupltd.com

### Color Quick Reference
- Primary Navy: `navy-900` (#102a43)
- Accent Gold: `gold-500` (#f59e0b)
- Background: `warm-50` (#fafaf9)
