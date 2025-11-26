---
description: 'Describe what this custom agent does and when to use it.'
tools: ['edit', 'runNotebooks', 'search', 'new', 'runCommands', 'runTasks', 'microsoft/playwright-mcp/*', 'Azure MCP/search', 'Copilot Container Tools/*', 'Microsoft Docs/*', 'pylance mcp server/*', 'vscode.mermaid-chat-features/renderMermaidDiagram', 'usages', 'vscodeAPI', 'problems', 'changes', 'testFailure', 'openSimpleBrowser', 'fetch', 'githubRepo', 'memory', 'github.vscode-pull-request-github/copilotCodingAgent', 'github.vscode-pull-request-github/issue_fetch', 'github.vscode-pull-request-github/suggest-fix', 'github.vscode-pull-request-github/searchSyntax', 'github.vscode-pull-request-github/doSearch', 'github.vscode-pull-request-github/renderIssues', 'github.vscode-pull-request-github/activePullRequest', 'github.vscode-pull-request-github/openPullRequest', 'ms-azuretools.vscode-apimanagement/get-available-apim-policies', 'ms-azuretools.vscode-azure-github-copilot/azure_get_azure_verified_module', 'ms-azuretools.vscode-azure-github-copilot/azure_recommend_custom_modes', 'ms-azuretools.vscode-azure-github-copilot/azure_query_azure_resource_graph', 'ms-azuretools.vscode-azure-github-copilot/azure_get_auth_context', 'ms-azuretools.vscode-azure-github-copilot/azure_set_auth_context', 'ms-azuretools.vscode-azure-github-copilot/azure_get_dotnet_template_tags', 'ms-azuretools.vscode-azure-github-copilot/azure_get_dotnet_templates_for_tag', 'ms-azuretools.vscode-azureresourcegroups/azureActivityLog', 'ms-python.python/getPythonEnvironmentInfo', 'ms-python.python/getPythonExecutableCommand', 'ms-python.python/installPythonPackage', 'ms-python.python/configurePythonEnvironment', 'ms-windows-ai-studio.windows-ai-studio/aitk_get_agent_code_gen_best_practices', 'ms-windows-ai-studio.windows-ai-studio/aitk_get_ai_model_guidance', 'ms-windows-ai-studio.windows-ai-studio/aitk_get_agent_model_code_sample', 'ms-windows-ai-studio.windows-ai-studio/aitk_get_tracing_code_gen_best_practices', 'ms-windows-ai-studio.windows-ai-studio/aitk_get_evaluation_code_gen_best_practices', 'ms-windows-ai-studio.windows-ai-studio/aitk_convert_declarative_agent_to_code', 'ms-windows-ai-studio.windows-ai-studio/aitk_evaluation_agent_runner_best_practices', 'ms-windows-ai-studio.windows-ai-studio/aitk_evaluation_planner', 'extensions', 'todos', 'runSubagent', 'runTests']
---
# Alara Group Website - AI Coding Instructions

## Project Overview
This is a static marketing website for **Alara Group Ltd**, an AI-powered business consultancy. The site targets B2B clients in insurance, defense, technology, healthcare, and professional services sectors.

## Technology Stack
- **HTML5** with semantic markup
- **Tailwind CSS** via CDN (`https://cdn.tailwindcss.com`) with inline configuration
- **Google Fonts**: Inter (headings), Open Sans (body text)
- **Hosting**: Cloudflare Pages (static deployment)
- **Forms**: Formspree for contact form handling

## Design System

### Color Palette (defined in Tailwind config)
```
navy-50 to navy-950   → Primary brand colors (dark backgrounds, text)
gold-50 to gold-900   → Accent/CTA colors (buttons, highlights)
warm-50 to warm-200   → Background neutrals
```

### Typography
- Headings: `font-heading` (Inter) - use for h1-h6, stats, brand elements
- Body: `font-body` (Open Sans) - use for paragraphs, descriptions

### Key UI Patterns
- Buttons: `bg-gradient-to-r from-gold-500 to-gold-600 rounded-full` with hover states
- Cards: `bg-white rounded-2xl p-8 shadow-lg border border-navy-100`
- Section spacing: `py-24` for major sections
- Max content width: `max-w-7xl mx-auto px-4 sm:px-6 lg:px-8`

## File Structure
```
/index.html          → Homepage with hero, mission, expertise preview
/about.html          → Team bios (Cindy & David Levitt), approach
/services.html       → Detailed service offerings
/markets.html        → Industry verticals served
/blog.html           → Insights/articles listing
/contact.html        → Contact form with Formspree
/css/styles.css      → Custom styles (minimal, Tailwind handles most)
/WEBSITE-GUIDE.md    → Client documentation for editing/hosting
```

## Content Guidelines
- **No em-dashes or in-text hyphens** - use commas or restructure sentences
- Tone: Professional yet welcoming, never clinical or bland
- Avoid generic marketing speak; be specific about AI and strategy services
- Founders: Cindy G. Levitt and David Levitt (husband-wife team)

## Development Commands
```powershell
# Preview locally (use any static server)
npx serve .

# Deploy to Cloudflare Pages
# Push to GitHub → automatic deployment via Cloudflare Pages integration
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
- X/Twitter: `https://www.x.com/alaragroupltd`
- Email: `info@alaragroupltd.com`

## When Adding New Pages
1. Copy the nav and footer from index.html
2. Update the active nav link class to `text-gold-600 border-b-2 border-gold-500`
3. Maintain consistent section padding (`py-24`)
4. Use established card and button patterns
