# SERVPRO Invoice Audit Control Panel

## Project Overview
Web-based control panel that configures and generates automation prompts for the SERVPRO Dash ERP system. The generated prompts drive Claude browser automation (Computer Use) to audit invoices across multiple offices and phases.

## Architecture
- **Single-page app**: `src/index.html` — self-contained HTML/CSS/JS (no build step)
- **No framework dependencies** — vanilla JS, CSS custom properties for theming
- **Fonts**: Google Fonts (Bebas Neue, IBM Plex Mono, IBM Plex Sans)

## Running Locally
```bash
npx serve src          # serves on port 3000
# or just open src/index.html directly in a browser
```

## Key Concepts
- **Office Target**: Which SERVPRO office(s) to audit (NE Dallas, Boise, McCall, Reno, or All)
- **Update Cap**: Max number of invoice date updates per automation run
- **Ratio Threshold**: Minimum Invoice/Estimate ratio for a job to qualify for update
- **Phases**: Job lifecycle stages to include (Invoice Pending, Completed–No Paperwork, WIP, Pre Production, Pending Sales)
- **Division Exclusions**: Divisions to skip (Recon 2.0/3.0 excluded by default)

## Workflow
1. User configures settings in the control panel
2. Clicks "Generate Prompt" to produce the automation prompt
3. Copies prompt to clipboard
4. Pastes into Claude in Chrome to execute against Dash ERP

## Code Conventions
- CSS uses custom properties defined in `:root` for all colors
- All UI state managed in plain JS (no state library)
- Prompt template is a JS template literal in `generatePrompt()`
