# Alara Group Website Guide

This comprehensive guide covers everything you need to use, maintain, edit, and deploy the Alara Group website. Whether you are updating content, adding new pages, or troubleshooting issues, this guide has you covered.

---

## Table of Contents

1. [Understanding Your Website](#understanding-your-website)
2. [Using the Website](#using-the-website)
3. [Quick Start for Editors](#quick-start-for-editors)
4. [File Structure](#file-structure)
5. [Editing Content](#editing-content)
6. [Design System Reference](#design-system-reference)
7. [Page by Page Guide](#page-by-page-guide)
8. [Adding New Content](#adding-new-content)
9. [Contact Form Setup](#contact-form-setup)
10. [Deployment](#deployment)
11. [Troubleshooting](#troubleshooting)
12. [Quick Reference](#quick-reference)

---

## Understanding Your Website

### What You Have

The Alara Group website is a modern, professional marketing site built with:

- **HTML5**: The structure and content of each page
- **Tailwind CSS**: A utility framework that handles all styling
- **Formspree**: A service that processes contact form submissions
- **Cloudflare Pages**: Hosting that deploys automatically from GitHub

### Why This Approach

This setup was chosen because:

1. **No maintenance burden**: No databases, no server updates, no security patches
2. **Fast loading**: Static HTML loads instantly anywhere in the world
3. **Easy editing**: Content is in plain HTML files you can edit directly
4. **Automatic deployment**: Push changes to GitHub and they go live automatically
5. **No recurring costs**: Cloudflare Pages free tier handles typical business traffic

### What You Can Change Yourself

- All text content on every page
- Contact information and social links
- Adding new blog posts or insight articles
- Basic layout changes within existing patterns
- Adding new pages using existing templates

### What Requires Developer Help

- Major design changes or new visual styles
- New interactive features or functionality
- Changes to the color palette or typography
- Technical integrations with other systems

---

## Using the Website

### Navigation

The website has six main pages, accessible from the navigation bar:

| Page | URL | Purpose |
|------|-----|---------|
| Home | `index.html` | First impression, overview of capabilities |
| About Us | `about.html` | Team bios, company story, approach |
| Services | `services.html` | Detailed service offerings |
| Markets | `markets.html` | Industries served with specific expertise |
| Insights | `blog.html` | Thought leadership articles |
| Contact | `contact.html` | Contact form and information |

### Mobile Experience

The site is fully responsive. On mobile devices:
- The navigation collapses into a hamburger menu (three lines)
- Tap the menu icon to show/hide navigation links
- All content adapts to smaller screens automatically

### Contact Form

When visitors submit the contact form:
1. Their information goes to Formspree
2. You receive an email notification (configure in Formspree dashboard)
3. Submissions are stored in your Formspree account for reference

---

## Quick Start for Editors

### Preview Changes Locally

Before pushing changes live, preview them on your computer:

**Option 1: Using Node.js (Recommended)**
```powershell
# Navigate to the project folder
cd "C:\path\to\Alara-Group"

# Start a local server
npx serve .
```
Open your browser to `http://localhost:3000`

**Option 2: Using Python**
```powershell
cd "C:\path\to\Alara-Group"
python -m http.server 8000
```
Open your browser to `http://localhost:8000`

**Option 3: Using VS Code Live Server Extension**
1. Install the "Live Server" extension in VS Code
2. Right click any HTML file
3. Select "Open with Live Server"

### Make a Simple Text Change

1. Open the HTML file in any text editor (VS Code recommended)
2. Find the text using `Ctrl+F` (search)
3. Edit the text directly
4. Save the file (`Ctrl+S`)
5. Refresh your local preview to verify
6. Commit and push to deploy (see [Deployment](#deployment))

### Deploy Your Changes

```powershell
# Stage all changes
git add .

# Commit with a message describing what you changed
git commit -m "Updated homepage hero text"

# Push to GitHub (triggers automatic deployment)
git push
```

---

## File Structure

```
Alara-Group/
├── index.html              # Homepage
├── about.html              # About Us page
├── services.html           # Services page
├── markets.html            # Markets/Industries page
├── blog.html               # Insights/Blog listing page
├── contact.html            # Contact page with form
├── css/
│   └── styles.css          # Custom CSS styles
├── images/                 # Image files (create when needed)
├── WEBSITE-GUIDE.md        # This guide
├── SOCIAL-MEDIA-GUIDE.md   # Social media setup guide
└── README.md               # Project overview
```

### What Each File Does

**HTML Pages**
- Each `.html` file is a complete page
- They all share the same navigation and footer
- Content is directly in the HTML (no separate content files)

**CSS Styles**
- `css/styles.css` contains custom styles beyond Tailwind
- Most styling comes from Tailwind CSS classes in the HTML
- Edit this file for site wide style changes

---

## Editing Content

### Content Guidelines

**Writing Style**
- Professional yet welcoming tone
- Specific and confident, not generic
- Avoid em dashes (—) and in text hyphens
- Use commas or restructure sentences instead

**Examples**

Instead of: `AI-powered solutions that transform your business`  
Write: `AI solutions that transform your business`

Instead of: `We offer end-to-end services — from strategy to implementation`  
Write: `We offer comprehensive services, from strategy to implementation`

### Editing Text

1. Open the HTML file
2. Find the text you want to change (use `Ctrl+F` to search)
3. Edit the text between the HTML tags
4. Save and preview

**Example:**
```html
<!-- Find this -->
<h1 class="font-display text-4xl">Old Headline</h1>

<!-- Change to -->
<h1 class="font-display text-4xl">New Headline</h1>
```

### Editing Links

To change where a link goes:
```html
<!-- Find the href attribute -->
<a href="old-url.html" class="...">Link Text</a>

<!-- Change the href value -->
<a href="new-url.html" class="...">Link Text</a>
```

### Adding Images

1. Create an `images` folder if it does not exist
2. Add your image file (use `.jpg`, `.png`, or `.webp`)
3. Use descriptive filenames: `team-photo.jpg` not `IMG_1234.jpg`
4. Add the image in HTML:

```html
<img 
    src="images/your-image.jpg" 
    alt="Description of what the image shows" 
    class="rounded-2xl w-full"
>
```

**Image Best Practices:**
- Optimize images before uploading (compress them)
- Keep file sizes under 500KB when possible
- Use descriptive alt text for accessibility
- Match aspect ratios of existing placeholder images

### Updating Social Links

Social links appear in the footer of every page. To update:

1. Open each HTML file
2. Find the social media section (near the bottom)
3. Update the `href` value with your actual profile URLs

```html
<a href="https://www.linkedin.com/company/alara-group-ltd" ...>
```

**Current Placeholders:**
- LinkedIn: `https://www.linkedin.com/company/alara-group-ltd`
- Facebook: `https://www.facebook.com/alaragroupltd`
- X (Twitter): `https://www.x.com/alaragroupltd`
- Email: `info@alaragroupltd.com`

---

## Design System Reference

### Color Palette

The site uses a sophisticated color scheme defined in each HTML file's Tailwind config:

| Color Group | CSS Classes | Usage |
|-------------|-------------|-------|
| **Slate** | `slate-50` to `slate-950` | Dark tones for text, headers, backgrounds |
| **Ember** | `ember-50` to `ember-900` | Warm orange accent for CTAs, highlights |
| **Sage** | `sage-50` to `sage-900` | Muted green for subtle accents |
| **Cream** | `cream-50` to `cream-200` | Warm off white backgrounds |

**Key Color Uses:**
- `slate-900` / `slate-950`: Dark text, dark sections
- `ember-500` / `ember-600`: Buttons, accent text, highlights
- `cream-50`: Main page backgrounds
- `white`: Cards, form backgrounds

### Typography

Three font families are used:

| Font | CSS Class | Usage |
|------|-----------|-------|
| **Playfair Display** | `font-display` | Large headlines, quotes |
| **Space Grotesk** | `font-heading` | Subheadings, labels, buttons |
| **Plus Jakarta Sans** | `font-body` | Body text, descriptions |

### Common UI Patterns

**Primary Button (CTA)**
```html
<a href="contact.html" class="bg-gradient-to-r from-ember-500 to-ember-600 text-white px-8 py-4 rounded-full font-heading font-semibold text-lg hover:from-ember-600 hover:to-ember-700 transition-all shadow-lg shadow-ember-500/25">
    Button Text
</a>
```

**Secondary Button**
```html
<a href="about.html" class="border-2 border-slate-200 text-slate-700 px-8 py-4 rounded-full font-heading font-medium hover:border-ember-500 hover:text-ember-600 transition-all">
    Button Text
</a>
```

**Card**
```html
<div class="bg-white rounded-2xl p-8 shadow-lg border border-slate-100">
    <!-- Card content -->
</div>
```

**Section with Background**
```html
<section class="py-24 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <!-- Section content -->
    </div>
</section>
```

**Dark Section**
```html
<section class="py-24 bg-gradient-to-br from-slate-900 via-slate-800 to-sage-900">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <!-- Use text-white and text-slate-300 for text -->
    </div>
</section>
```

---

## Page by Page Guide

### Homepage (index.html)

**Sections:**
1. Hero: Main headline and intro
2. Stats: Key numbers/metrics
3. Mission: What the company does
4. Expertise: Service categories
5. CTA: Call to action

**Common Edits:**
- Update hero headline and subtext
- Change stat numbers and labels
- Modify mission statement
- Update expertise descriptions

### About Page (about.html)

**Sections:**
1. Page header: Title and intro
2. Story: Company background
3. Team: Founder bios
4. Approach: How you work

**Common Edits:**
- Update founder bios and credentials
- Refresh company story/history
- Add team member photos (when available)

### Services Page (services.html)

**Sections:**
1. Header: Services overview
2. Service cards: Individual service descriptions
3. CTA: Contact prompt

**Common Edits:**
- Update service descriptions
- Add or remove services
- Modify pricing or engagement info

### Markets Page (markets.html)

**Sections:**
1. Header: Industries intro
2. Industry blocks: Insurance, Defense, Technology, Healthcare, Professional Services

**Common Edits:**
- Update industry specific expertise
- Add new industries
- Modify use cases and applications

### Insights Page (blog.html)

**Sections:**
1. Header: Blog intro
2. Featured article: Highlighted post
3. Article grid: List of articles
4. Newsletter signup

**Adding a New Article:**
1. Copy an existing article card
2. Update the title, description, date, and read time
3. Update the category badge
4. Add link to full article (when you create one)

**Article Card Template:**
```html
<article class="bg-white rounded-2xl border border-slate-100 overflow-hidden hover:shadow-xl transition-shadow duration-300 group">
    <div class="h-48 bg-gradient-to-br from-sage-100 to-sage-200 relative overflow-hidden">
        <div class="absolute bottom-4 left-4">
            <span class="bg-white/90 text-sage-700 text-xs font-heading font-medium px-3 py-1 rounded-full">Category</span>
        </div>
    </div>
    <div class="p-6">
        <h3 class="font-display text-xl font-bold text-slate-900 mb-3 group-hover:text-ember-600 transition-colors">Article Title</h3>
        <p class="text-slate-600 mb-4 leading-relaxed">Brief description of the article content.</p>
        <div class="flex items-center justify-between text-sm text-slate-400">
            <span>Month Year</span>
            <span>X min read</span>
        </div>
    </div>
</article>
```

### Contact Page (contact.html)

**Sections:**
1. Header: Contact intro
2. Contact info: Email, social
3. Contact form
4. FAQ section

**Common Edits:**
- Update contact information
- Modify form fields
- Update FAQ questions and answers

---

## Adding New Content

### Adding a New Page

1. Copy an existing page as a template (about.html works well)
2. Rename the file: `new-page.html`
3. Update the page content
4. Update the navigation link in the new page:

**Active state (for the new page itself):**
```html
<a href="new-page.html" class="text-ember-600 border-b-2 border-ember-500 font-medium pb-1">New Page</a>
```

5. Add navigation link to ALL other pages:
```html
<a href="new-page.html" class="text-slate-600 hover:text-ember-600 transition-colors">New Page</a>
```

### Adding Individual Blog Articles

For full blog articles:

1. Create a new file: `blog/article-name.html`
2. Copy the structure from an existing page
3. Create article content with proper heading hierarchy
4. Link from the blog listing page

### Adding Team Photos

1. Save photos at a consistent size (e.g., 400x400 pixels, square)
2. Place in the `images/` folder
3. Update the about.html team section:

```html
<img src="images/team-member-name.jpg" alt="Team Member Name, Title" class="w-48 h-48 rounded-full object-cover mx-auto mb-6">
```

---

## Contact Form Setup

### Setting Up Formspree

1. **Get Your Form ID**:
   - Go to [formspree.io](https://formspree.io/) and create a free account.
   - Click "+ New Form".
   - Name it "Alara Website Contact".
   - You will get an endpoint URL like `https://formspree.io/f/xkqjbpqz`.
   - The last part (`xkqjbpqz`) is your **Form ID**.

2. **Update the Code**:
   - Open `contact.html`.
   - Find line ~138: `<form action="https://formspree.io/f/YOUR_FORM_ID" ...>`.
   - Replace `YOUR_FORM_ID` with your actual ID.
   - Save and deploy.

### Configuring Email Notifications

In your Formspree dashboard:
1. Go to your form settings.
2. Enable email notifications.
3. Add notification recipients (e.g., `info@alaragroupltd.com`).
4. (Optional) Customize the notification email template.

---

## SEO & Analytics Setup

### Search Engine Optimization (SEO)

The site is pre-configured with meta tags for Google, Facebook (Open Graph), and Twitter.

**To optimize further:**
1. **Images**: Ensure `images/og-image.jpg` exists. This is the image people see when you share the site on LinkedIn. It should be 1200x630 pixels.
2. **Descriptions**: Edit the `<meta name="description">` tag in each HTML file to match your latest messaging.

### Analytics (Plausible)

We recommend Plausible Analytics because it is privacy-friendly (no cookie banners needed) and simple.

1. Create an account at [plausible.io](https://plausible.io).
2. Add your domain `alaragroupltd.com`.
3. You will get a script snippet.
4. We have already placed a commented-out snippet in the `<head>` of every page.
5. Uncomment it and ensure the `data-domain` matches yours.

```html
<!-- Remove the comments (<!-- and -->) around this line in every HTML file -->
<script defer data-domain="alaragroupltd.com" src="https://plausible.io/js/script.js"></script>
```

---

## Managing the Blog

### Adding a New Post

1. **Create the File**:
   - Navigate to the `blog/` folder.
   - Copy `why-most-ai-strategies-fail.html` and rename it (e.g., `new-article.html`).

2. **Update Content**:
   - Open the new file.
   - Update the `<title>`, meta description, and OG tags in the `<head>`.
   - Update the Header section (Title, Date, Read Time).
   - Write your content in the `<article>` section.

3. **Link it**:
   - Open `blog.html`.
   - Copy one of the existing article cards.
   - Update the link (`href`), title, and summary.

---

### Form Fields Explained

The current form collects:
- First Name (required)
- Last Name (required)
- Email (required)
- Company (optional)
- Industry (dropdown)
- Interest area (dropdown)
- Message (text area)

To add a field:
```html
<div>
    <label for="newField" class="block text-sm font-heading font-medium text-slate-700 mb-2">Field Label</label>
    <input type="text" id="newField" name="newField" class="w-full px-4 py-3 rounded-xl border border-slate-200 focus:outline-none focus:ring-2 focus:ring-ember-500 focus:border-transparent transition-all" placeholder="Placeholder text">
</div>
```

---

## Deployment

### How Deployment Works

1. You make changes to files locally
2. You commit and push to GitHub
3. Cloudflare Pages detects the push
4. Cloudflare builds and deploys automatically
5. Changes are live in 1 to 3 minutes

### Deploying Changes

```powershell
# Navigate to project
cd "C:\path\to\Alara-Group"

# Check what changed
git status

# Stage all changes
git add .

# Commit with descriptive message
git commit -m "Brief description of what changed"

# Push to GitHub
git push
```

### First Time Cloudflare Setup

1. Go to [Cloudflare Pages](https://pages.cloudflare.com/)
2. Sign in or create account
3. Click "Create a project"
4. Select "Connect to Git"
5. Authorize GitHub access
6. Select the Alara-Group repository
7. Configure build settings:
   - Framework preset: None
   - Build command: (leave empty)
   - Build output directory: `/` or `.`
8. Click "Save and Deploy"

### Custom Domain Setup

1. In Cloudflare Pages dashboard, go to your project
2. Click "Custom domains"
3. Add your domain (e.g., `alaragroupltd.com`)
4. Follow DNS instructions (if domain is in Cloudflare, it auto configures)
5. Wait for SSL certificate (usually 15 minutes)

---

## Troubleshooting

### Changes Not Appearing

**Check deployment status:**
1. Go to Cloudflare Pages dashboard
2. Look for recent deployments
3. Check if deployment succeeded or failed

**Clear browser cache:**
- Windows: `Ctrl+Shift+R`
- Mac: `Cmd+Shift+R`
- Or open in private/incognito window

**Check you pushed to the right branch:**
```powershell
git branch  # Shows current branch
git push origin main  # Explicitly push to main
```

### Styling Looks Broken

Check that the Tailwind CDN script is in the `<head>`:
```html
<script src="https://cdn.tailwindcss.com"></script>
```

Ensure the Tailwind config block follows immediately after.

### Mobile Menu Not Working

Verify this script is at the bottom of your HTML, before `</body>`:
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

1. Check the Formspree form ID is correct
2. Verify required fields have the `required` attribute
3. Check browser console for errors (F12 > Console)
4. Test with a simple submission

### Images Not Loading

1. Verify the file path is correct (case sensitive)
2. Check the file exists in the specified location
3. Ensure file extension matches exactly

---

## Quick Reference

### Key Information

| Item | Value |
|------|-------|
| Company | Alara Group Ltd |
| Primary Email | info@alaragroupltd.com |
| Founders | Cindy G. Levitt, David Levitt |
| LinkedIn | linkedin.com/company/alara-group-ltd |
| Facebook | facebook.com/alaragroupltd |
| X (Twitter) | x.com/alaragroupltd |

### Color Quick Reference

| Use | Class |
|-----|-------|
| Dark background | `bg-slate-900` |
| Dark text | `text-slate-900` |
| Accent/CTA | `bg-ember-500` / `text-ember-500` |
| Light background | `bg-cream-50` |
| White card | `bg-white` |

### Typography Quick Reference

| Use | Class |
|-----|-------|
| Large headline | `font-display text-4xl font-bold` |
| Section title | `font-display text-3xl font-bold` |
| Subheading | `font-heading font-semibold` |
| Body text | `font-body text-lg text-slate-600` |
| Small text | `text-sm text-slate-500` |

### Spacing Quick Reference

| Use | Class |
|-----|-------|
| Section padding | `py-24` |
| Container width | `max-w-7xl mx-auto px-4 sm:px-6 lg:px-8` |
| Card padding | `p-8` |
| Grid gap | `gap-8` |

---

## Support

For website questions or issues:
- Email: info@alaragroupltd.com

For hosting/deployment issues:
- Cloudflare Status: https://www.cloudflarestatus.com/
- Cloudflare Support: https://support.cloudflare.com/
