# Alara Group Website: AI Coding Instructions

## Project Overview

This is a static marketing website for **Alara Group Ltd**, an AI strategy consultancy. The site targets B2B clients in insurance, defense, technology, healthcare, and professional services sectors.

## Technology Stack

- **HTML5** with semantic markup
- **Tailwind CSS** via CDN (`https://cdn.tailwindcss.com`) with inline configuration
- **Google Fonts**: Playfair Display (display), Space Grotesk (headings), Plus Jakarta Sans (body)
- **Hosting**: Cloudflare Pages (static deployment)
- **Forms**: Formspree for contact form handling

## Design System

### Color Palette (defined in Tailwind config)

| Color Family | Purpose |
|--------------|---------|
| slate-50 to slate-950 | Primary dark tones (backgrounds, text) |
| ember-50 to ember-900 | Accent and CTA colors (buttons, highlights) |
| sage-50 to sage-900 | Muted green accents |
| cream-50 to cream-200 | Warm background neutrals |

### Typography

- Display: `font-display` (Playfair Display) for large headlines
- Headings: `font-heading` (Space Grotesk) for subheadings, labels, buttons
- Body: `font-body` (Plus Jakarta Sans) for paragraphs and descriptions

### Key UI Patterns

- Buttons: `bg-gradient-to-r from-ember-500 to-ember-600 rounded-full` with hover states
- Cards: `bg-white rounded-2xl p-8 shadow-lg border border-slate-100`
- Section spacing: `py-24` for major sections
- Max content width: `max-w-7xl mx-auto px-4 sm:px-6 lg:px-8`

## File Structure

```
/index.html          → Homepage with hero, mission, expertise preview
/about.html          → Team bios (Cindy and David Levitt), approach
/services.html       → Detailed service offerings
/markets.html        → Industry verticals served
/blog.html           → Insights and articles listing
/contact.html        → Contact form with Formspree
/css/styles.css      → Custom styles (minimal, Tailwind handles most)
/WEBSITE-GUIDE.md    → Detailed documentation for editing and hosting
/GETTING-STARTED.md  → Beginner friendly setup guide
```

## Content Guidelines

- **No em dashes or unnecessary hyphens**: Use commas or restructure sentences
- Tone: Professional yet welcoming, never clinical or bland
- Avoid generic marketing speak; be specific about AI and strategy services
- Founders: Cindy G. Levitt and David Levitt (husband and wife team)

## Development Commands

```powershell
# Preview locally (use any static server)
npx serve .

# Deploy to Cloudflare Pages
# Push to GitHub and automatic deployment follows
```

## Navigation Structure

All pages share the same nav component with these links:

- Home → index.html
- About Us → about.html  
- Services → services.html
- Markets → markets.html
- Insights → blog.html
- Contact Us → contact.html (CTA button style)

## Social Links

- LinkedIn: `https://www.linkedin.com/company/alara-group-ltd`
- Facebook: `https://www.facebook.com/alaragroupltd`
- X (Twitter): `https://www.x.com/alaragroupltd`
- Email: `info@alaragroupltd.com`

## When Adding New Pages

1. Copy the nav and footer from index.html
2. Update the active nav link class to `text-ember-600 border-b-2 border-ember-500`
3. Maintain consistent section padding (`py-24`)
4. Use established card and button patterns

