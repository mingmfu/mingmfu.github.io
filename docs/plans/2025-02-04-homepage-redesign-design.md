# Academic Homepage Redesign - Design Document

> **Date:** 2025-02-04  
> **Subject:** Dr. Ming Fu Academic Homepage Redesign

## Executive Summary

**Current State:** HTML 4.01 table-based layout, outdated styling, limited content sections  
**Target:** Modern, professional academic homepage befitting a research director at Huawei Fields Lab  
**Approach:** Clean, minimalist design with emphasis on research impact and publications

---

## Design Philosophy

### Visual Direction: Modern Academic

Inspired by leading academic institutions (MIT, Stanford, CMU) and industry research labs:

- **Color Palette:** 
  - Primary: Deep navy blue (#1a365d) - authority, trust
  - Secondary: Warm gray (#4a5568) - sophistication
  - Accent: Subtle gold/amber (#d69e2e) - excellence, awards
  - Background: Clean white (#ffffff) with light gray (#f7fafc) sections
  
- **Typography:**
  - Headings: Inter or system sans-serif, bold weight
  - Body: System font stack for optimal readability
  - Monospace for technical terms
  
- **Layout Principles:**
  - Maximum content width: 900px for optimal reading
  - Generous whitespace (padding: 2-3rem between sections)
  - Clear visual hierarchy
  - Responsive design (mobile-first)

---

## Architecture

### Technology Stack
- **HTML5** semantic markup
- **CSS3** with CSS Grid and Flexbox
- **No JavaScript dependencies** (except optional analytics)
- **Static site** - fast, secure, maintainable

### File Structure
```
/
├── index.html              # Main homepage
├── css/
│   └── styles.css          # All styles
├── assets/
│   └── (images if needed)
├── papers/                 # Existing PDFs (keep)
├── research/               # Existing research content (keep)
└── fuming-cv.pdf           # Existing CV (keep)
```

---

## Section Design

### 1. Header / Hero Section

**Purpose:** Immediate identity and credibility

**Content:**
- Professional photo (left)
- Name and title (right)
- Affiliation: Huawei Fields Lab Director
- Contact: Email, Location
- Quick links: CV, Google Scholar, GitHub (if applicable)

**Design:**
- Two-column layout on desktop, stacked on mobile
- Subtle bottom border or shadow
- Photo with rounded corners or circular frame

### 2. About / Research Interests

**Purpose:** Concise research narrative

**Content:**
- One paragraph research statement
- Key research areas as tags/badges:
  - Operating Systems
  - Concurrency Verification
  - Formal Verification
  - Weak Memory Models
  - OS Architecture

**Design:**
- Clean paragraph text
- Research areas as styled tags
- Link to full CV

### 3. Selected Publications

**Purpose:** Showcase research impact and productivity

**Content:**
- Top-tier venues highlighted (OSDI, SOSP, ASPLOS, SIGGRAPH Asia, POPL)
- Awards noted (Distinguished Paper Award)
- Links to papers, slides, talks
- Group by year (most recent first)

**Design:**
- Each paper as a card or clean list item
- Venue name bolded
- Award badges for distinguished papers
- Hover effects on links
- Year grouping with subtle headers

### 4. Footer

**Purpose:** Professional closure and contact

**Content:**
- Copyright notice
- Last updated date
- Contact email

**Design:**
- Subtle gray background
- Centered or left-aligned text
- Minimal styling

---

## Responsive Breakpoints

- **Desktop:** > 768px - Full two-column layout
- **Tablet:** 768px - Adjusted spacing, may stack
- **Mobile:** < 640px - Single column, full-width sections

---

## Implementation Notes

### CSS Architecture
- Use CSS custom properties (variables) for colors
- Mobile-first media queries
- Flexbox for component layouts
- CSS Grid for overall page structure

### Accessibility
- Semantic HTML5 elements (header, main, section, article, footer)
- Proper heading hierarchy (h1 > h2 > h3)
- Alt text for images
- Sufficient color contrast (WCAG AA)
- Focus states for interactive elements

### Performance
- Single CSS file (no external dependencies)
- System fonts (no web font loading)
- Optimized images
- Minimal JavaScript

---

## Content Migration

### Keep from Current Site:
- All paper PDFs in /papers/
- Research subdirectory content
- CV PDF
- Photos (ming.jpg, mfu.jpg)

### Update:
- index.html - complete rewrite
- stylesheet.css - complete rewrite

---

## Success Criteria

1. **Professional Appearance:** Looks like a top-tier academic's homepage
2. **Readability:** Easy to scan publications and find information
3. **Mobile-Friendly:** Works well on all devices
4. **Fast Loading:** < 1 second initial paint
5. **Maintainable:** Easy to add new papers

---

## Next Steps

1. Create implementation plan with writing-plans skill
2. Build new HTML structure
3. Implement CSS styling
4. Migrate and format publication list
5. Test responsiveness
6. Deploy

