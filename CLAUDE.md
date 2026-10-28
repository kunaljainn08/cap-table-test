# CapView: project notes for Claude Code

## What this is
CapView is a startup cap table and fundraise simulator for Indian users. People enter a startup's data and get results on screen plus a downloadable report.

## Structure
- Everything lives in one self-contained file: `index.html` (HTML, CSS and JavaScript inline). No build step, no framework.
- Hosted on GitHub Pages (Settings → Pages → Deploy from a branch → main → /(root)).
- External scripts load only from cdnjs (SheetJS for Excel, html2pdf.js for the PDF report).

## Inputs
Company at founding (name, founders and their shares, ESOP pool %, liquidation seniority), mentors/advisors (stake % and when granted), funding rounds (pre-money, investment, pool target %, liquidation preference multiple, participating), exit value slider.

## Outputs
- Summary cards, Ownership (stacked bars + table), Round Economics (price per share, step-up, effective pre-money after the option pool shuffle), Exit Waterfall (stacked or pari passu, convert-or-preference), How It Works.
- Hero donut and "pizza story" at the top update live from the user's numbers; hovering or tapping a slice pops it out and shows name, stake, shares and value.
- Downloads: a designed 3-page A4 PDF report (html2pdf, SVGs converted to images first) and a 5-sheet Excel workbook.

## Decisions already made (keep these)
- Opens with a worked example (Example SaaS startup). "Clear & Enter My Own" empties it; "Reset to Example" restores it. Example vs user data is labelled.
- "Get My Results" scrolls to the top and highlights the donut.
- Light and dark mode via a toggle in the nav; theme remembered in localStorage (only the theme).
- Sticky nav: section links scroll with an offset so headings aren't hidden on phones; "Open Simulator" shortens to "Simulator" on small screens.
- "Learn the Concepts" uses fixed round numbers and is not linked to the simulator.
- Footer line: "No founders were harmed in the making of this website. Diluted, maybe."
- Plain, simple English in all UI text. Indian number formatting (₹, crore, lakh).

## Roadmap (agreed next steps)
1. Real cap tables of famous Indian startups (Zomato, Nykaa, Swiggy, Lenskart…) rebuilt from their DRHPs' "history of share capital", with sources and a "reconstructed from public data" label, plus a "build from any DRHP" upload.
2. "What are my ESOPs worth?" calculator for employees (reuses the exit waterfall; Indian tax at exercise and sale).
3. Reverse valuation planner: "I want to keep X% after this round; what valuation do I need?", with flags for founder-unfriendly terms.

## How to test
Open `index.html` in a browser. Check the example loads, Clear works, Get My Results scrolls up, the PDF and Excel downloads work, dark mode looks right, and the layout works at phone width (about 390px) with no sideways scrolling.
