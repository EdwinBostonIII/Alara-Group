# Alara Group Website Guide

This comprehensive guide covers everything you need to edit, maintain, and update the Alara Group website. Whether you want to change some text, add a new article, or understand how things work, this guide has you covered.

If you are completely new to this project, we recommend reading `GETTING-STARTED.md` first for the basic setup instructions.

---

## Table of Contents

1. [Understanding Your Website](#understanding-your-website)
2. [Website Navigation](#website-navigation)
3. [Quick Editing Guide](#quick-editing-guide)
4. [Editing Content](#editing-content)
5. [Design System Reference](#design-system-reference)
6. [Page Guides](#page-guides)
7. [Adding New Content](#adding-new-content)
8. [Contact Form](#contact-form)
9. [Analytics Setup](#analytics-setup)
10. [Publishing Changes](#publishing-changes)
11. [Troubleshooting](#troubleshooting)
12. [Quick Reference](#quick-reference)

---

## Understanding Your Website

### What Your Website Is Made Of

Your website uses simple, reliable technology:

- **HTML5**: The structure and content of each page (you will edit these files)
- **Tailwind CSS**: A styling system that makes everything look polished
- **Formspree**: A service that handles contact form submissions
- **Cloudflare Pages**: Free hosting that makes your site fast and secure

### Why We Chose This Setup

This approach has several advantages:

1. **No ongoing maintenance**: There are no databases to update or security patches to install
2. **Fast loading**: Static HTML loads instantly for visitors anywhere in the world
3. **Easy editing**: Content lives in plain text files you can edit directly
4. **Automatic publishing**: Push changes to GitHub and they go live automatically
5. **No monthly costs**: Cloudflare Pages handles typical business traffic for free

### What You Can Edit Yourself

- All text content on every page
- Contact information and social media links
- Blog posts and insight articles
- Basic layout changes using existing patterns
- New pages using existing templates as a starting point

### When You Might Need Help

- Major design changes or new visual styles
- New interactive features or functionality
- Changes to the color palette or typography
- Technical integrations with other systems

---

## Website Navigation

Your website has six main pages:

| Page | File | Purpose |
|------|------|---------|
| Home | `index.html` | First impression, value proposition, overview |
| About Us | `about.html` | Your story, team bios, approach |
| Services | `services.html` | What you offer and how you work |
| Markets | `markets.html` | Industries you serve with specific expertise |
| Insights | `blog.html` | Thought leadership articles |
| Contact | `contact.html` | Contact form and information |

### Mobile Experience

The website automatically adapts to phones and tablets:

- Navigation collapses into a menu icon (three horizontal lines)
- Tapping the icon shows or hides the navigation links
- All content adjusts to fit smaller screens

### Contact Form

When a visitor submits the contact form:

1. Their information is sent to Formspree
2. You receive an email notification
3. Submissions are stored in your Formspree account for reference

---

## Quick Editing Guide

### Previewing Changes Locally

Before publishing changes, preview them on your computer:

#### Using the Live Server Extension (Recommended)

1. Install the "Live Server" extension in VS Code (one time setup)
2. Right click any HTML file in the sidebar
3. Select "Open with Live Server"
4. Your browser will open showing your site
5. Changes you save will automatically appear in the preview

#### Using a Command Line Server

Open a terminal in VS Code and run:

```powershell
npx serve .
```

Then open your browser to `http://localhost:3000`

### Making a Simple Text Change

1. Open the HTML file you want to edit
2. Press `Ctrl+F` to search for the text you want to change
3. Edit the text directly (leave HTML tags like `<p>` and `</p>` intact)
4. Press `Ctrl+S` to save
5. Preview to verify your change looks correct

### Publishing Your Changes

After saving your edits, run these three commands in the terminal:

```powershell
git add .
git commit -m "Brief description of what you changed"
git push
```

Your changes will be live within one to two minutes.

---

## Editing Content

### Writing Style Guidelines

**Keep the tone professional yet welcoming:**

- Be specific and confident, not vague or generic
- Write as if you are speaking to a trusted colleague
- Use plain language; explain technical terms if you must use them

**Avoid em dashes and complex hyphens:**

Instead of: `AI-powered solutions that transform your business`
Write: `AI solutions that transform your business`

Instead of: `We offer end-to-end services — from strategy to implementation`
Write: `We offer comprehensive services, from strategy to implementation`

### Editing Text

Find the HTML file you want to change and locate the text:

1. Open the file in VS Code
2. Use `Ctrl+F` to search for specific words
3. Edit the text between the HTML tags
4. Save the file

**Example:**

```html
<!-- Before -->
<h1 class="font-display text-4xl">Original Headline</h1>

<!-- After -->
<h1 class="font-display text-4xl">Your New Headline</h1>
```

### Editing Links

To change where a link points:

```html
<!-- Find the href attribute -->
<a href="old-page.html" class="...">Link Text</a>

<!-- Change the href value -->
<a href="new-page.html" class="...">Link Text</a>
```

### Adding Images

1. Create an `images` folder in your project (if it does not exist)
2. Add your image file using a descriptive name like `team-photo.jpg`
3. Add the image in HTML:

```html
<img 
    src="images/your-image.jpg" 
    alt="Description of what the image shows" 
    class="rounded-2xl w-full"
>
```

**Image Tips:**

- Compress images before uploading to keep file sizes small (under 500KB is ideal)
- Use descriptive alt text for accessibility
- Match the aspect ratios of existing placeholder images when replacing them

### Updating Social Links

Social links appear in the footer of every page. To update them:

1. Open each HTML file
2. Search for the social media section (near the bottom)
3. Update the `href` values with your actual profile URLs
4. Save all files and publish

**Current Links:**

- LinkedIn: `https://www.linkedin.com/company/alara-group-ltd`
- Facebook: `https://www.facebook.com/alaragroupltd`
- X (Twitter): `https://www.x.com/alaragroupltd`
- Email: `info@alaragroupltd.com`

---

## Design System Reference

### Color Palette

The site uses a sophisticated color scheme:

| Color Family | CSS Classes | How It Is Used |
|--------------|-------------|----------------|
| **Slate** | `slate-50` to `slate-950` | Dark tones for text, headers, backgrounds |
| **Ember** | `ember-50` to `ember-900` | Warm orange for buttons, highlights, accents |
| **Sage** | `sage-50` to `sage-900` | Muted green for subtle accents |
| **Cream** | `cream-50` to `cream-200` | Warm off white page backgrounds |

**Common Color Uses:**

- `slate-900` or `slate-950`: Dark text and dark section backgrounds
- `ember-500` or `ember-600`: Buttons, accent text, highlighted elements
- `cream-50`: Main page backgrounds
- `white`: Cards and form backgrounds

### Typography

Three font families create the visual hierarchy:

| Font | CSS Class | Where It Is Used |
|------|-----------|------------------|
| **Playfair Display** | `font-display` | Large headlines, quotes |
| **Space Grotesk** | `font-heading` | Subheadings, labels, buttons |
| **Plus Jakarta Sans** | `font-body` | Body text, descriptions |

### Common UI Patterns

#### Primary Button (Call to Action)

```html
<a href="contact.html" class="bg-gradient-to-r from-ember-500 to-ember-600 text-white px-8 py-4 rounded-full font-heading font-semibold text-lg hover:from-ember-600 hover:to-ember-700 transition-all shadow-lg shadow-ember-500/25">
    Button Text
</a>
```

#### Secondary Button

```html
<a href="about.html" class="border-2 border-slate-200 text-slate-700 px-8 py-4 rounded-full font-heading font-medium hover:border-ember-500 hover:text-ember-600 transition-all">
    Button Text
</a>
```

#### Content Card

```html
<div class="bg-white rounded-2xl p-8 shadow-lg border border-slate-100">
    <!-- Your card content here -->
</div>
```

#### Standard Section

```html
<section class="py-24 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <!-- Your section content here -->
    </div>
</section>
```

#### Dark Section

```html
<section class="py-24 bg-gradient-to-br from-slate-900 via-slate-800 to-sage-900">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <!-- Use text-white and text-slate-300 for text in dark sections -->
    </div>
</section>
```

---

## Page Guides

### Homepage (index.html)

**What It Contains:**

1. Hero section: Main headline, introductory text, and call to action buttons
2. Stats: Key numbers that demonstrate the AI adoption gap
3. Mission: Why Alara Group exists and what you stand for
4. Expertise preview: Overview of your service categories
5. Call to action: Prompt to get in touch

**Common Edits:**

- Update the hero headline and supporting text
- Change the statistics (with sources)
- Modify the mission statement
- Update the expertise descriptions

### About Page (about.html)

**What It Contains:**

1. Page header: Title and introduction
2. Your story: How Alara Group came to be
3. Team section: Founder bios and backgrounds
4. Your approach: How you work with clients

**Common Edits:**

- Update founder bios and credentials
- Refresh the company story
- Add team photos when available

### Services Page (services.html)

**What It Contains:**

1. Header: Overview of your service philosophy
2. Service cards: Individual service descriptions
3. Call to action: Invitation to discuss needs

**Common Edits:**

- Update service descriptions
- Add or remove services
- Modify engagement details

### Markets Page (markets.html)

**What It Contains:**

1. Header: Your industry expertise introduction
2. Industry sections: Insurance, Defense, Technology, Healthcare, Professional Services

**Common Edits:**

- Update industry specific expertise
- Add new industries
- Modify use cases and examples

### Insights Page (blog.html)

**What It Contains:**

1. Header: Introduction to your thought leadership
2. Featured article: Highlighted piece
3. Article grid: List of available articles
4. Newsletter signup: Email capture (if configured)

### Contact Page (contact.html)

**What It Contains:**

1. Header: Contact introduction
2. Contact information: Email and social links
3. Contact form: Submission form
4. FAQ section: Common questions

---

## Adding New Content

### Adding a New Page

1. Copy an existing page as a template (about.html works well)
2. Rename the file with a descriptive name like `new-page.html`
3. Update the page content
4. Update the navigation in the new page to show the active state:

```html
<a href="new-page.html" class="text-ember-600 border-b-2 border-ember-500 font-medium pb-1">New Page</a>
```

5. Add navigation links to ALL other pages:

```html
<a href="new-page.html" class="text-slate-600 hover:text-ember-600 transition-colors">New Page</a>
```

### Adding a Blog Article

1. Navigate to the `blog/` folder
2. Copy an existing article file as a template
3. Rename it with a descriptive name (use lowercase and hyphens, like `new-article-title.html`)
4. Update the content, title, meta descriptions, and date
5. Open `blog.html` and add a card linking to your new article

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

### Adding Team Photos

1. Save photos at a consistent size (400 by 400 pixels works well for headshots)
2. Place them in the `images/` folder
3. Update the about.html team section:

```html
<img src="images/team-member-name.jpg" alt="Team Member Name, Title" class="w-48 h-48 rounded-full object-cover mx-auto mb-6">
```

---

## Contact Form

### Setting Up Formspree

1. Go to formspree.io and create a free account
2. Click "New Form" and name it "Alara Website Contact"
3. Copy your Form ID (the code at the end of your endpoint URL)
4. Open `contact.html` and find the form action attribute
5. Replace `YOUR_FORM_ID` with your actual Form ID
6. Save and publish

### Configuring Email Notifications

In your Formspree dashboard:

1. Go to your form settings
2. Enable email notifications
3. Add notification recipients (like info@alaragroupltd.com)
4. Optionally customize the notification email template

### Form Fields

The current form collects:

- First Name (required)
- Last Name (required)
- Email (required)
- Company (optional)
- Industry (dropdown)
- Interest area (dropdown)
- Message (text area)

---

## Analytics Setup

We recommend Plausible Analytics because it is privacy friendly (no cookie consent banners needed) and easy to understand.

### Setting Up Plausible

1. Create an account at plausible.io
2. Add your domain: alaragroupltd.com
3. Copy the script snippet they provide
4. The HTML files already have a placeholder for this script in the head section
5. Uncomment the script line and ensure the domain matches:

```html
<script defer data-domain="alaragroupltd.com" src="https://plausible.io/js/script.js"></script>
```

### Search Engine Optimization

Each page includes meta tags for Google, Facebook, and Twitter sharing:

- Create an image at `images/og-image.jpg` (1200 by 630 pixels) for social sharing
- Edit the meta description tag in each HTML file to match your current messaging

---

## Publishing Changes

### How Publishing Works

1. You make changes to files on your computer
2. You commit and push those changes to GitHub
3. Cloudflare Pages detects the new changes
4. Cloudflare automatically updates your live website
5. Changes appear within one to three minutes

### Step by Step Publishing

Open a terminal in VS Code and run these commands:

```powershell
# See what files you changed
git status

# Stage all your changes
git add .

# Commit with a descriptive message
git commit -m "Updated homepage headline and services descriptions"

# Push to GitHub (this triggers the automatic update)
git push
```

### First Time Cloudflare Setup

If your site is not yet connected to Cloudflare Pages:

1. Go to pages.cloudflare.com and sign in
2. Click "Create a project"
3. Select "Connect to Git"
4. Authorize GitHub access
5. Select your Alara Group repository
6. Configure build settings:
   - Framework preset: None
   - Build command: Leave empty
   - Build output directory: `/` or `.`
7. Click "Save and Deploy"

### Custom Domain Setup

1. In your Cloudflare Pages dashboard, go to your project
2. Click "Custom domains"
3. Add your domain (alaragroupltd.com)
4. Follow the DNS instructions provided
5. Wait for the SSL certificate (usually about 15 minutes)

---

## Troubleshooting

### Changes Not Appearing on the Live Site

**Check deployment status:**

1. Go to your Cloudflare Pages dashboard
2. Look for recent deployments
3. Check if the deployment succeeded or failed

**Clear your browser cache:**

Press `Ctrl+Shift+R` to force a full refresh, or open the site in a private/incognito window.

**Verify you pushed to the correct branch:**

```powershell
git branch
git push origin main
```

### Styling Looks Broken

Make sure the Tailwind script is in the head section of your HTML:

```html
<script src="https://cdn.tailwindcss.com"></script>
```

The Tailwind configuration block should follow immediately after.

### Mobile Menu Not Working

Verify this script exists at the bottom of your HTML, just before the closing body tag:

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

1. Check that the Formspree Form ID is correct
2. Verify required fields have the `required` attribute
3. Check for errors in the browser console (press F12, then click Console)
4. Test with a simple submission

### Images Not Loading

1. Verify the file path is correct (paths are case sensitive)
2. Check that the file exists in the specified location
3. Ensure the file extension matches exactly

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

| Purpose | CSS Class |
|---------|-----------|
| Dark background | `bg-slate-900` |
| Dark text | `text-slate-900` |
| Accent button | `bg-ember-500` |
| Accent text | `text-ember-500` |
| Light background | `bg-cream-50` |
| White card | `bg-white` |

### Typography Quick Reference

| Purpose | CSS Classes |
|---------|-------------|
| Large headline | `font-display text-4xl font-bold` |
| Section title | `font-display text-3xl font-bold` |
| Subheading | `font-heading font-semibold` |
| Body text | `font-body text-lg text-slate-600` |
| Small text | `text-sm text-slate-500` |

### Spacing Quick Reference

| Purpose | CSS Class |
|---------|-----------|
| Section padding | `py-24` |
| Container width | `max-w-7xl mx-auto px-4 sm:px-6 lg:px-8` |
| Card padding | `p-8` |
| Grid gap | `gap-8` |

---

## Need More Help?

For website questions: info@alaragroupltd.com

For hosting issues:
- Cloudflare Status: cloudflarestatus.com
- Cloudflare Support: support.cloudflare.com

For Formspree issues:
- Formspree Help: help.formspree.io
