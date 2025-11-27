# Getting Started with Your Alara Group Website

Welcome! This guide will walk you through everything you need to know about your website project. We have written it to be friendly and approachable, with no technical jargon left unexplained.

Take your time reading through this. There is no rush, and you can always come back to any section later.

---

## Table of Contents

1. [What You Have (The Big Picture)](#what-you-have-the-big-picture)
2. [Understanding How Your Website Works](#understanding-how-your-website-works)
3. [Setting Up Your Computer](#setting-up-your-computer)
4. [Making Your First Edit](#making-your-first-edit)
5. [Publishing Changes to Your Live Website](#publishing-changes-to-your-live-website)
6. [Setting Up Your Contact Form](#setting-up-your-contact-form)
7. [Connecting Your Domain](#connecting-your-domain)
8. [Common Tasks](#common-tasks)
9. [Getting Help](#getting-help)

---

## What You Have (The Big Picture)

### Your Website

You have a professional, modern website for Alara Group. It includes six pages:

1. **Home** (index.html): Your main landing page with your value proposition
2. **About Us** (about.html): Your story, your approach, and your bios
3. **Services** (services.html): What you offer to clients
4. **Markets** (markets.html): The industries you serve
5. **Insights** (blog.html): Thought leadership articles
6. **Contact** (contact.html): A form for potential clients to reach you

### Your Methodology Library

In the `METHODOLOGIES/` folder, you have an extensive collection of consulting frameworks, industry playbooks, and scenario guides. These represent your intellectual property and consulting approach.

### Your Support Documents

Several guides help you manage your business:

- **WEBSITE-GUIDE.md**: Detailed technical reference for website editing
- **SOCIAL-MEDIA-GUIDE.md**: Copy and paste content for social profiles
- **MARKETING-STRATEGY.md**: Growth and lead generation ideas

---

## Understanding How Your Website Works

Let us explain this in plain terms, so you know what is happening behind the scenes.

### Where Your Website Lives

Your website is hosted on **Cloudflare Pages**, a service that stores your website files and delivers them to visitors anywhere in the world. When someone types "alaragroupltd.com" into their browser, Cloudflare sends them your website.

**Why this is good for you:**
- It costs $0 per month (Cloudflare's free tier is generous)
- It is extremely fast (Cloudflare has servers worldwide)
- It is secure (automatic HTTPS encryption)
- It requires zero maintenance from you

### How Updates Work

Your website files are stored in two places:

1. **GitHub**: A service that stores and tracks all changes to your files (like a backup system with history)
2. **Cloudflare Pages**: The service that actually shows your website to visitors

When you make a change and "push" it to GitHub, Cloudflare automatically notices and updates your live website within a minute or two. You do not need to do anything special; it just happens.

### What the Files Actually Are

Your website is made of simple text files:

- **HTML files** (.html): These contain your actual content, like the text on each page. You can open and edit these just like a Word document.
- **CSS files** (.css): These control how things look (colors, fonts, spacing). You probably will not need to touch these.
- **Markdown files** (.md): These are your guides and documentation. They are also just text files.

---

## Setting Up Your Computer

Before you can make changes to your website, you need a few free tools on your computer. This is a one time setup.

### Step 1: Install Visual Studio Code

Visual Studio Code (VS Code) is a free text editor that makes editing website files easy. It is made by Microsoft and used by millions of people.

1. Go to: https://code.visualstudio.com/
2. Click the big "Download" button
3. Run the installer and follow the prompts
4. Accept all the default options

### Step 2: Install Git

Git is a tool that tracks changes to your files and sends them to GitHub. Think of it as a "save and sync" system.

1. Go to: https://git-scm.com/downloads
2. Download the version for Windows
3. Run the installer
4. **Important:** During installation, when asked about the default editor, choose "Use Visual Studio Code as Git's default editor"
5. Accept the defaults for everything else

### Step 3: Set Up Your GitHub Account

GitHub is where your website files are stored online.

1. If you do not have a GitHub account, create one at: https://github.com/
2. Use an email address you check regularly (you will get notifications here)
3. Choose a simple username you will remember

### Step 4: Connect Git to Your GitHub Account

Open VS Code and then open the built in terminal:

1. Click "View" in the top menu
2. Click "Terminal"
3. A panel will appear at the bottom of VS Code

Type these commands one at a time, pressing Enter after each. Replace the example information with your own:

```
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### Step 5: Download Your Website Project

1. Open VS Code
2. Press `Ctrl+Shift+P` to open the command palette
3. Type "Git: Clone" and select it
4. Paste your repository URL (ask your developer for this if you do not have it)
5. Choose a folder on your computer to save the project (your Desktop is fine)
6. When prompted, click "Open" to open the project

Congratulations! You now have everything set up. You only need to do this once.

---

## Making Your First Edit

Let us walk through making a simple change to your website. We will change some text on your homepage.

### Step 1: Open Your Project

1. Open VS Code
2. Click "File" then "Open Folder"
3. Navigate to your Alara Group folder and click "Select Folder"
4. You should see all your files in the left sidebar

### Step 2: Open the File You Want to Edit

1. In the left sidebar, click on `index.html`
2. The file will open in the main editing area

### Step 3: Find the Text You Want to Change

1. Press `Ctrl+F` to open the search box
2. Type a few words from the text you want to find
3. VS Code will highlight all matches
4. Click on a match to jump to that location

### Step 4: Make Your Change

1. Click on the text you want to change
2. Delete the old text and type your new text
3. Be careful not to delete any of the code tags (the parts that look like `<p>` or `</h1>`)

**Example:**
If you see this:
```html
<h1>Old Headline Text</h1>
```

You can change it to:
```html
<h1>Your New Headline Text</h1>
```

### Step 5: Save Your File

Press `Ctrl+S` to save. The white dot next to the filename (indicating unsaved changes) will disappear.

### Step 6: Preview Your Change (Optional)

Before publishing, you can preview your changes locally:

1. Install the "Live Server" extension in VS Code:
   - Click the Extensions icon in the left sidebar (looks like four squares)
   - Search for "Live Server"
   - Click "Install" on the one by Ritwick Dey
2. Right click on `index.html` in the sidebar
3. Select "Open with Live Server"
4. Your browser will open showing your website
5. Any changes you save will automatically appear in the preview

---

## Publishing Changes to Your Live Website

Once you are happy with your changes, here is how to make them live.

### Step 1: Open the Terminal

In VS Code, click "View" then "Terminal" (or press `Ctrl+``)

### Step 2: Stage Your Changes

Type this command and press Enter:

```
git add .
```

This tells Git "I want to include all my changes."

### Step 3: Commit Your Changes

Type this command, but replace the message with a description of what you changed:

```
git commit -m "Updated homepage headline"
```

The message in quotes helps you remember what each change was for.

### Step 4: Push to GitHub

Type this command and press Enter:

```
git push
```

The first time you do this, your browser may open asking you to log in to GitHub. Do so, and authorize VS Code to access your account.

### Step 5: Wait for Deployment

Within one to two minutes, Cloudflare will automatically update your live website. Visit alaragroupltd.com to see your changes.

---

## Setting Up Your Contact Form

Your website has a contact form that sends submissions to your email. Here is how to set it up.

### Step 1: Create a Formspree Account

1. Go to: https://formspree.io/
2. Click "Get Started" and create a free account
3. Use your business email (info@alaragroupltd.com is ideal)

### Step 2: Create a New Form

1. After logging in, click "New Form"
2. Name it something like "Alara Website Contact"
3. Click "Create Form"

### Step 3: Get Your Form ID

After creating the form, you will see an endpoint URL like:
```
https://formspree.io/f/xkqjbpqz
```

The last part (`xkqjbpqz` in this example) is your Form ID. Copy it.

### Step 4: Add Your Form ID to the Website

1. Open `contact.html` in VS Code
2. Press `Ctrl+F` and search for `YOUR_FORM_ID`
3. Replace `YOUR_FORM_ID` with your actual Form ID
4. Save the file
5. Commit and push your changes (see the publishing section above)

### Step 5: Configure Email Notifications

1. In your Formspree dashboard, click on your form
2. Go to "Settings"
3. Under "Email Notifications," add the email addresses that should receive form submissions
4. Save your settings

Now, whenever someone fills out your contact form, you will receive an email.

---

## Connecting Your Domain

If your domain (alaragroupltd.com) is not yet connected to your website, here is how to set it up.

### If You Already Own the Domain

You need to point your domain to Cloudflare Pages. The exact steps depend on where you bought your domain (GoDaddy, Namecheap, Google Domains, etc.).

**General steps:**

1. Log in to your Cloudflare Pages dashboard
2. Go to your project settings
3. Click "Custom domains"
4. Add your domain name
5. Cloudflare will give you DNS records to add
6. Log in to your domain registrar and add those DNS records
7. Wait up to 24 hours for the changes to take effect

If this feels overwhelming, your domain registrar likely has customer support that can help you add DNS records.

### If You Need to Buy a Domain

1. Go to a domain registrar like Namecheap (https://www.namecheap.com/) or Google Domains
2. Search for "alaragroupltd.com"
3. Purchase it (typically $10 to $15 per year)
4. Follow the steps above to connect it to Cloudflare Pages

---

## Common Tasks

### Changing Text on a Page

1. Open the HTML file for that page
2. Find the text using `Ctrl+F`
3. Edit the text (leave the HTML tags like `<p>` and `</p>` intact)
4. Save, commit, and push

### Adding a New Blog Article

1. Copy the file `blog/why-most-ai-strategies-fail.html` as a template
2. Rename it to match your new article (use lowercase and hyphens, like `new-article-title.html`)
3. Open the new file and replace the content
4. Update the blog listing page (`blog.html`) to include a link to your new article
5. Save, commit, and push

### Updating Your Email or Social Links

These appear in the footer of every page. You will need to update them in each HTML file:

1. Open each HTML file one at a time
2. Search for the current email or social URL
3. Replace it with the new one
4. Save all files
5. Commit and push once at the end

### Adding Photos

1. Create an `images` folder in your project if it does not exist
2. Add your image files to that folder (use descriptive names like `cindy-headshot.jpg`)
3. In your HTML, add an image tag: `<img src="images/cindy-headshot.jpg" alt="Cindy G. Levitt">`
4. Save, commit, and push

---

## Getting Help

### If Something Goes Wrong

The `WEBSITE-GUIDE.md` file has a detailed troubleshooting section. Check there first.

### Common Issues and Solutions

**"I made a change but it is not showing on the live site"**
- Did you save the file? (Ctrl+S)
- Did you commit and push? (All three commands: add, commit, push)
- Wait two minutes; Cloudflare needs time to update

**"I accidentally broke something"**
- Git tracks all changes. You can undo mistakes.
- In VS Code, right click the file and select "Discard Changes" to undo unsaved edits
- If you already committed, contact your developer for help reverting

**"The website looks strange or broken"**
- You may have accidentally deleted an HTML tag
- Press `Ctrl+Z` repeatedly to undo recent changes
- If that does not work, you can restore the file from GitHub

### When to Contact a Developer

Some tasks are beyond simple editing:

- Changing the overall design or layout
- Adding new features or functionality
- Fixing complex technical issues
- Setting up integrations with other services

For these situations, you will want professional help.

---

## You Are Ready!

You now have everything you need to manage your Alara Group website. Remember:

- Start with small changes to build confidence
- Always preview before publishing when possible
- The guides in this folder are your reference; come back to them anytime
- It is okay to take it slow; there is no rush

Your website is a powerful tool for your business. With practice, editing it will become second nature.

Welcome to Alara Group's digital home!
