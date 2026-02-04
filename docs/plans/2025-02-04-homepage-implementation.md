# Academic Homepage Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Redesign Dr. Ming Fu's academic homepage with modern, professional styling befitting a research director

**Architecture:** Single-page static site with semantic HTML5, modern CSS3 using CSS Grid/Flexbox, mobile-first responsive design

**Tech Stack:** HTML5, CSS3 (no frameworks), system fonts, static files only

---

## Task 1: Create New CSS File Structure

**Files:**
- Create: `css/styles.css`
- Delete: `stylesheet.css` (will be replaced)

**Step 1: Create CSS directory and base file**

```bash
mkdir -p css
```

**Step 2: Write CSS foundation**

Create `css/styles.css` with:
- CSS custom properties (variables) for colors
- CSS reset and base styles
- Typography system
- Layout utilities

```css
/* CSS Custom Properties */
:root {
  /* Colors */
  --color-primary: #1a365d;
  --color-secondary: #4a5568;
  --color-accent: #d69e2e;
  --color-bg: #ffffff;
  --color-bg-alt: #f7fafc;
  --color-text: #2d3748;
  --color-text-light: #718096;
  --color-border: #e2e8f0;
  
  /* Typography */
  --font-sans: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  --font-mono: "SF Mono", Monaco, "Cascadia Code", "Roboto Mono", Consolas, "Courier New", monospace;
  
  /* Spacing */
  --space-xs: 0.25rem;
  --space-sm: 0.5rem;
  --space-md: 1rem;
  --space-lg: 1.5rem;
  --space-xl: 2rem;
  --space-2xl: 3rem;
  
  /* Layout */
  --max-width: 900px;
  --border-radius: 8px;
}

/* Reset */
*, *::before, *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

/* Base */
html {
  font-size: 16px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  font-family: var(--font-sans);
  font-size: 1rem;
  line-height: 1.6;
  color: var(--color-text);
  background-color: var(--color-bg);
}

/* Typography */
h1, h2, h3, h4, h5, h6 {
  font-weight: 700;
  line-height: 1.2;
  color: var(--color-primary);
}

h1 { font-size: 2rem; }
h2 { font-size: 1.5rem; margin-top: var(--space-2xl); margin-bottom: var(--space-lg); }
h3 { font-size: 1.25rem; }

p {
  margin-bottom: var(--space-md);
}

a {
  color: var(--color-primary);
  text-decoration: none;
  transition: color 0.2s ease;
}

a:hover {
  color: var(--color-accent);
  text-decoration: underline;
}

/* Layout */
.container {
  max-width: var(--max-width);
  margin: 0 auto;
  padding: 0 var(--space-lg);
}

section {
  padding: var(--space-xl) 0;
}

/* Utilities */
.text-muted { color: var(--color-text-light); }
.font-mono { font-family: var(--font-mono); }
```

**Step 3: Verify file created**

```bash
ls -la css/
cat css/styles.css | head -20
```

**Step 4: Commit**

```bash
git add css/
git commit -m "feat: add CSS foundation with design system"
```

---

## Task 2: Create Header/Hero Section Styles

**Files:**
- Modify: `css/styles.css` (append styles)

**Step 1: Add header styles**

Append to `css/styles.css`:

```css
/* Header / Hero Section */
.hero {
  padding: var(--space-2xl) 0;
  border-bottom: 1px solid var(--color-border);
  background-color: var(--color-bg);
}

.hero-content {
  display: grid;
  grid-template-columns: auto 1fr;
  gap: var(--space-xl);
  align-items: center;
}

.hero-photo {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  object-fit: cover;
  border: 3px solid var(--color-border);
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.hero-info h1 {
  font-size: 2.5rem;
  margin-bottom: var(--space-sm);
  color: var(--color-primary);
}

.hero-title {
  font-size: 1.125rem;
  color: var(--color-secondary);
  margin-bottom: var(--space-md);
  font-weight: 500;
}

.hero-affiliation {
  font-size: 1rem;
  color: var(--color-text-light);
  margin-bottom: var(--space-md);
}

.hero-contact {
  display: flex;
  flex-wrap: wrap;
  gap: var(--space-md);
  font-size: 0.95rem;
}

.hero-contact span {
  display: flex;
  align-items: center;
  gap: var(--space-xs);
}

.hero-links {
  margin-top: var(--space-md);
  display: flex;
  gap: var(--space-md);
}

.hero-links a {
  display: inline-flex;
  align-items: center;
  gap: var(--space-xs);
  padding: var(--space-sm) var(--space-md);
  background-color: var(--color-bg-alt);
  border-radius: var(--border-radius);
  font-size: 0.9rem;
  font-weight: 500;
  transition: all 0.2s ease;
}

.hero-links a:hover {
  background-color: var(--color-primary);
  color: white;
  text-decoration: none;
}

/* Mobile responsive */
@media (max-width: 640px) {
  .hero-content {
    grid-template-columns: 1fr;
    text-align: center;
  }
  
  .hero-photo {
    width: 120px;
    height: 120px;
    margin: 0 auto;
  }
  
  .hero-info h1 {
    font-size: 2rem;
  }
  
  .hero-contact {
    justify-content: center;
  }
  
  .hero-links {
    justify-content: center;
  }
}
```

**Step 2: Verify styles added**

```bash
grep -A 5 "Hero Section" css/styles.css
```

**Step 3: Commit**

```bash
git add css/styles.css
git commit -m "feat: add hero section styles"
```

---

## Task 3: Create About/Research Section Styles

**Files:**
- Modify: `css/styles.css` (append styles)

**Step 1: Add about section styles**

Append to `css/styles.css`:

```css
/* About / Research Section */
.about {
  background-color: var(--color-bg-alt);
}

.about-content {
  max-width: 800px;
}

.about-text {
  font-size: 1.05rem;
  line-height: 1.7;
  margin-bottom: var(--space-lg);
}

.research-areas {
  display: flex;
  flex-wrap: wrap;
  gap: var(--space-sm);
  margin-top: var(--space-md);
}

.research-tag {
  display: inline-block;
  padding: var(--space-xs) var(--space-md);
  background-color: var(--color-bg);
  border: 1px solid var(--color-border);
  border-radius: 20px;
  font-size: 0.9rem;
  color: var(--color-secondary);
  font-weight: 500;
}

.research-tag:hover {
  border-color: var(--color-accent);
  color: var(--color-accent);
}
```

**Step 2: Commit**

```bash
git add css/styles.css
git commit -m "feat: add about section styles with research tags"
```

---

## Task 4: Create Publications Section Styles

**Files:**
- Modify: `css/styles.css` (append styles)

**Step 1: Add publications styles**

Append to `css/styles.css`:

```css
/* Publications Section */
.publications {
  background-color: var(--color-bg);
}

.pub-year {
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--color-primary);
  margin: var(--space-xl) 0 var(--space-md) 0;
  padding-bottom: var(--space-sm);
  border-bottom: 2px solid var(--color-border);
}

.pub-year:first-child {
  margin-top: 0;
}

.pub-list {
  list-style: none;
  padding: 0;
}

.pub-item {
  padding: var(--space-md) 0;
  border-bottom: 1px solid var(--color-border);
}

.pub-item:last-child {
  border-bottom: none;
}

.pub-title {
  font-size: 1.05rem;
  font-weight: 600;
  color: var(--color-text);
  margin-bottom: var(--space-xs);
  line-height: 1.4;
}

.pub-title a {
  color: var(--color-primary);
}

.pub-title a:hover {
  color: var(--color-accent);
}

.pub-authors {
  font-size: 0.95rem;
  color: var(--color-text-light);
  margin-bottom: var(--space-xs);
}

.pub-venue {
  font-size: 0.9rem;
  color: var(--color-secondary);
  font-style: italic;
}

.pub-venue strong {
  font-style: normal;
  color: var(--color-primary);
}

.pub-award {
  display: inline-block;
  margin-left: var(--space-sm);
  padding: 2px 8px;
  background-color: var(--color-accent);
  color: white;
  font-size: 0.75rem;
  font-weight: 700;
  border-radius: 4px;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.pub-links {
  margin-top: var(--space-sm);
  display: flex;
  gap: var(--space-md);
  font-size: 0.9rem;
}

.pub-links a {
  color: var(--color-text-light);
}

.pub-links a:hover {
  color: var(--color-accent);
}
```

**Step 2: Commit**

```bash
git add css/styles.css
git commit -m "feat: add publications section styles with awards"
```

---

## Task 5: Create Footer Styles

**Files:**
- Modify: `css/styles.css` (append styles)

**Step 1: Add footer styles**

Append to `css/styles.css`:

```css
/* Footer */
.footer {
  background-color: var(--color-bg-alt);
  padding: var(--space-xl) 0;
  border-top: 1px solid var(--color-border);
  text-align: center;
  color: var(--color-text-light);
  font-size: 0.9rem;
}

.footer a {
  color: var(--color-secondary);
}

.footer a:hover {
  color: var(--color-accent);
}
```

**Step 2: Commit**

```bash
git add css/styles.css
git commit -m "feat: add footer styles"
```

---

## Task 6: Create New HTML Structure

**Files:**
- Create: `index.html` (backup old one first)

**Step 1: Backup old index**

```bash
cp index.html index.html.old
```

**Step 2: Write new HTML**

Create new `index.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Dr. Ming Fu - Director of Huawei Fields Lab. Research interests: Operating Systems, Concurrency Verification, Formal Verification.">
  <meta name="keywords" content="Operating System, Multicore Concurrency, Formal Verification, OS Verification">
  <title>Dr. Ming Fu - Huawei Fields Lab</title>
  <link rel="stylesheet" href="css/styles.css">
</head>
<body>

  <!-- Header / Hero Section -->
  <header class="hero">
    <div class="container">
      <div class="hero-content">
        <img src="ming.jpg" alt="Dr. Ming Fu" class="hero-photo">
        <div class="hero-info">
          <h1>Dr. Ming Fu</h1>
          <p class="hero-title">Director of Huawei Fields Lab</p>
          <p class="hero-affiliation">Huawei Technologies Co., Ltd.</p>
          
          <div class="hero-contact">
            <span>📍 Hangzhou, China</span>
            <span>✉️ ming.fu AT huawei DOT com</span>
          </div>
          
          <div class="hero-links">
            <a href="fuming-cv.pdf" target="_blank">📄 CV</a>
          </div>
        </div>
      </div>
    </div>
  </header>

  <main>
    
    <!-- About Section -->
    <section class="about">
      <div class="container">
        <div class="about-content">
          <h2>Research</h2>
          <p class="about-text">
            I am interested in industry-oriented research on concurrency verification, weak memory consistency, 
            OS architecture, and formal verification of operating systems. The goal is to build highly efficient 
            and reliable OS rendering services and Web engines.
          </p>
          
          <div class="research-areas">
            <span class="research-tag">Operating Systems</span>
            <span class="research-tag">Concurrency Verification</span>
            <span class="research-tag">Formal Verification</span>
            <span class="research-tag">Weak Memory Models</span>
            <span class="research-tag">OS Architecture</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Publications Section -->
    <section class="publications">
      <div class="container">
        <h2>Selected Publications</h2>

        <h3 class="pub-year">2025</h3>
        <ul class="pub-list">
          
          <li class="pub-item">
            <div class="pub-title">
              <a href="https://dl.acm.org/doi/10.1145/3757377.3763965" target="_blank">StereoFG: Generating Stereo Frames from Centered Feature Stream</a>
            </div>
            <div class="pub-authors">Chenyu Zuo, Yazhen Yuan, Zhizhen Wu, Zhijian Liu, Jingzhen Lan, Ming Fu, Yuchi Huo, Rui Wang</div>
            <div class="pub-venue">SIGGRAPH Asia 2025, December 16–18, 2025</div>
          </li>

          <li class="pub-item">
            <div class="pub-title">
              <a href="papers/osdi25-final255.pdf" target="_blank">OS Rendering Service Made Parallel with Out-of-Order Execution and In-Order Commit</a>
            </div>
            <div class="pub-authors">Yuanpei Wu, Dong Du, Chao Xu, Yubin Xia, Yang Yu, Ming Fu, Binyu Zang, Haibo Chen</div>
            <div class="pub-venue"><strong>OSDI 2025</strong>, July 7–9, 2025</div>
          </li>

          <li class="pub-item">
            <div class="pub-title">
              <a href="papers/dvsync.pdf" target="_blank">D-VSync: Decoupled Rendering and Displaying for Smartphone Graphics</a>
            </div>
            <div class="pub-authors">Yuanpei Wu, Dong Du, Chao Xu, Yubin Xia, Ming Fu, Binyu Zang, Haibo Chen</div>
            <div class="pub-venue"><strong>ASPLOS 2025</strong>, March 2025</div>
          </li>

          <li class="pub-item">
            <div class="pub-title">
              <a href="papers/btrace.pdf" target="_blank">Enabling Efficient Mobile Tracing with BTrace</a>
            </div>
            <div class="pub-authors">Jiawei Wang, Nian Liu, Arnau Casadevall-Saiz, Yutao Liu, Diogo Behrens, Ming Fu, Ning Jia, Hermann Härtig, Haibo Chen</div>
            <div class="pub-venue"><strong>ASPLOS 2025</strong>, March 2025</div>
          </li>

        </ul>

        <h3 class="pub-year">2023</h3>
        <ul class="pub-list">

          <li class="pub-item">
            <div class="pub-title">
              <a href="papers/osdi23_bwos.pdf" target="_blank">BWoS: Formally Verified Block-based Work Stealing for Parallel Processing</a>
            </div>
            <div class="pub-authors">Jiawei Wang, Bohdan Trach, Ming Fu*, Diogo Behrens, Jonathan Schwender, Yutao Liu, Jitang Lei, Viktor Vafeiadis, Hermann Härtig, Haibo Chen</div>
            <div class="pub-venue"><strong>OSDI 2023</strong>, July 10–12, 2023</div>
            <div class="pub-links">
              <a href="papers/osdi23_bwos_slides.pdf" target="_blank">Slides</a>
            </div>
          </li>

          <li class="pub-item">
            <div class="pub-title">
              <a href="papers/atomig.pdf" target="_blank">AtoMig: Automatically Migrating Millions Lines of Code from TSO to WMM</a>
            </div>
            <div class="pub-authors">Martin Beck, Koustubha Bhat, Lazar Stričević, Geng Chen, Diogo Behrens, Ming Fu*, Viktor Vafeiadis, Haibo Chen, Hermann Härtig</div>
            <div class="pub-venue"><strong>ASPLOS 2023</strong>, March 2023</div>
          </li>

        </ul>

        <h3 class="pub-year">2022</h3>
        <ul class="pub-list">

          <li class="pub-item">
            <div class="pub-title">
              <a href="papers/BBQ.pdf" target="_blank">BBQ: A Block-based Bounded Queue for Exchanging Data and Profiling</a>
            </div>
            <div class="pub-authors">Jiawei Wang, Diogo Behrens, Ming Fu*, Lilith Oberhauser, Jonas Oberhauser, Jitang Lei, Geng Chen, Hermann Härtig, Haibo Chen</div>
            <div class="pub-venue"><strong>USENIX ATC 2022</strong>, July 11–13, 2022</div>
          </li>

          <li class="pub-item">
            <div class="pub-title">
              <a href="https://arxiv.org/abs/2111.15240" target="_blank">Verifying and Optimizing Compact NUMA-Aware Locks on Weak Memory Models</a>
            </div>
            <div class="pub-authors">Antonio Paolillo, Hernán Ponce-de-León, Thomas Haas, Diogo Behrens, Rafael Chehab, Ming Fu, Roland Meyer</div>
            <div class="pub-venue">Technical Note, arXiv, July 9, 2022</div>
          </li>

        </ul>

        <h3 class="pub-year">2021</h3>
        <ul class="pub-list">

          <li class="pub-item">
            <div class="pub-title">
              <a href="papers/clof.pdf" target="_blank">CLoF: A Compositional Lock Framework for Multi-level NUMA Systems</a>
            </div>
            <div class="pub-authors">Rafael Lourenco de Lima Chehab, Antonio Paolillo, Diogo Behrens, Ming Fu*, Hermann Härtig, Haibo Chen</div>
            <div class="pub-venue"><strong>SOSP 2021</strong>, October 25-28, 2021</div>
          </li>

          <li class="pub-item">
            <div class="pub-title">
              <a href="papers/netys-2021.pdf" target="_blank">Verifying and Optimizing the HMCS Lock for Arm Servers</a>
            </div>
            <div class="pub-authors">Jonas Oberhauser, Lilith Oberhauser, Antonio Paolillo, Diogo Behrens, Ming Fu, Viktor Vafeiadis</div>
            <div class="pub-venue"><strong>NETYS 2021</strong>, May 2021</div>
          </li>

          <li class="pub-item">
            <div class="pub-title">
              <a href="papers/asplos2021-vsync.pdf" target="_blank">VSync: Push-Button Verification and Optimization for Synchronization Primitives on Weak Memory Models</a>
              <span class="pub-award">Distinguished Paper</span>
            </div>
            <div class="pub-authors">Jonas Oberhauser, Rafael Lourenco de Lima Chehab, Diogo Behrens, Ming Fu*, Antonio Paolillo, Lilith Oberhauser, Koustubha Bhat, Yuzhong Wen, Haibo Chen, Jaeho Kim, Viktor Vafeiadis</div>
            <div class="pub-venue"><strong>ASPLOS 2021</strong>, April 2021</div>
            <div class="pub-links">
              <a href="https://b23.tv/6rg68v" target="_blank">Short Talk</a>
              <a href="https://b23.tv/TlnTyA" target="_blank">Full Talk</a>
            </div>
          </li>

        </ul>

        <h3 class="pub-year">2020</h3>
        <ul class="pub-list">

          <li class="pub-item">
            <div class="pub-title">
              <a href="papers/sparc.pdf" target="_blank">Formalizing SPARCv8 Instruction Set Architecture in Coq</a>
            </div>
            <div class="pub-authors">Jiawei Wang, Ming Fu, Lei Qiao, Xinyu Feng</div>
            <div class="pub-venue">Science of Computer Programming, 187: 102371, 2020</div>
          </li>

        </ul>

        <h3 class="pub-year">2019</h3>
        <ul class="pub-list">

          <li class="pub-item">
            <div class="pub-title">
              <a href="papers/sosp19-atomfs.pdf" target="_blank">Using Concurrent Relational Logic with Helper for Verifying the AtomFS File System</a>
            </div>
            <div class="pub-authors">Mo Zou, Haoran Ding, Dong Du, Ming Fu, Ronghui Gu, Haibo Chen</div>
            <div class="pub-venue"><strong>SOSP 2019</strong>, October 27-30, 2019</div>
          </li>

        </ul>

        <h3 class="pub-year">2016</h3>
        <ul class="pub-list">

          <li class="pub-item">
            <div class="pub-title">
              <a href="research/certiucos/" target="_blank">A Practical Verification Framework for Preemptive OS Kernels</a>
            </div>
            <div class="pub-authors">Fengwei Xu, Ming Fu*, Xinyu Feng, Xiaoran Zhang, Hui Zhang, Zhaohui Li</div>
            <div class="pub-venue"><strong>CAV 2016</strong>, July 2016</div>
          </li>

        </ul>

        <h3 class="pub-year">2015</h3>
        <ul class="pub-list">

          <li class="pub-item">
            <div class="pub-title">
              <a href="papers/p97-cao.pdf" target="_blank">Practical Tactics for Verifying C Programs in Coq</a>
            </div>
            <div class="pub-authors">Jingyuan Cao, Ming Fu*, Xinyu Feng</div>
            <div class="pub-venue"><strong>CPP 2015</strong>, January 2015</div>
          </li>

        </ul>

        <h3 class="pub-year">2014</h3>
        <ul class="pub-list">

          <li class="pub-item">
            <div class="pub-title">
              <a href="papers/TOPLAS14_Preprint.pdf" target="_blank">Rely-Guarantee-Based Simulation for Compositional Verification of Concurrent Program Transformations</a>
            </div>
            <div class="pub-authors">Hongjin Liang, Xinyu Feng, Ming Fu</div>
            <div class="pub-venue">ACM Transactions on Programming Languages and Systems (TOPLAS), Vol. 36, No. 1, Article 3, March 2014</div>
          </li>

        </ul>

        <h3 class="pub-year">2013</h3>
        <ul class="pub-list">

          <li class="pub-item">
            <div class="pub-title">
              <a href="papers/32_02-Kouskoulas-Zero.pdf" target="_blank">Applying Mathematical Logic to Create Zero-Defect Software</a>
            </div>
            <div class="pub-authors">Yanni Kouskoulas, Ming Fu, Zhong Shao, Peter Kazanzides</div>
            <div class="pub-venue">Johns Hopkins APL Technical Digest, Volume 32, Number 2, 2013</div>
          </li>

        </ul>

        <h3 class="pub-year">2012</h3>
        <ul class="pub-list">

          <li class="pub-item">
            <div class="pub-title">
              <a href="papers/POPL2012.pdf" target="_blank">A Rely-Guarantee-Based Simulation for Verifying Concurrent Program Transformations</a>
            </div>
            <div class="pub-authors">Hongjin Liang, Xinyu Feng, Ming Fu</div>
            <div class="pub-venue"><strong>POPL 2012</strong>, January 2012</div>
          </li>

        </ul>

        <h3 class="pub-year">2010</h3>
        <ul class="pub-list">

          <li class="pub-item">
            <div class="pub-title">
              <a href="papers/concur10.pdf" target="_blank">Reasoning about Optimistic Concurrency Using a Program Logic for History</a>
            </div>
            <div class="pub-authors">Ming Fu, Yong Li, Xinyu Feng, Zhong Shao, Yu Zhang</div>
            <div class="pub-venue"><strong>CONCUR 2010</strong>, August 2010</div>
          </li>

        </ul>

      </div>
    </section>

  </main>

  <!-- Footer -->
  <footer class="footer">
    <div class="container">
      <p>© 2025 Dr. Ming Fu | <a href="mailto:ming.fu@huawei.com">ming.fu@huawei.com</a></p>
      <p class="text-muted">Last updated: February 2025</p>
    </div>
  </footer>

</body>
</html>
```

**Step 3: Verify new HTML**

```bash
head -30 index.html
grep -c "pub-item" index.html
```

**Step 4: Commit**

```bash
git add index.html index.html.old
git commit -m "feat: rewrite homepage with modern HTML5 structure"
```

---

## Task 7: Remove Old Stylesheet

**Files:**
- Delete: `stylesheet.css`

**Step 1: Remove old CSS**

```bash
rm stylesheet.css
```

**Step 2: Verify removal**

```bash
ls -la stylesheet.css 2>&1 || echo "File removed successfully"
```

**Step 3: Commit**

```bash
git rm stylesheet.css
git commit -m "chore: remove old stylesheet (replaced by css/styles.css)"
```

---

## Task 8: Test and Verify

**Files:**
- Test: `index.html` in browser or with validator

**Step 1: Validate HTML structure**

```bash
# Check for basic HTML structure
head -10 index.html
tail -10 index.html
```

**Step 2: Verify all links work**

```bash
# Check paper links exist
grep -o 'href="papers/[^"]*"' index.html | sort | uniq
grep -o 'href="[^"]*\.pdf"' index.html | sort | uniq
```

**Step 3: Check CSS loads correctly**

```bash
grep "css/styles.css" index.html
ls -la css/styles.css
```

**Step 4: Final verification**

```bash
# Count publication items
pub_count=$(grep -c "pub-item" index.html)
echo "Total publications: $pub_count"

# Check for required sections
echo "Checking sections:"
grep -c "hero" index.html && echo "✓ Hero section"
grep -c "about" index.html && echo "✓ About section"
grep -c "publications" index.html && echo "✓ Publications section"
grep -c "footer" index.html && echo "✓ Footer section"
```

**Step 5: Commit final changes**

```bash
git add -A
git commit -m "feat: complete homepage redesign with modern styling"
```

---

## Summary

This implementation plan creates a modern, professional academic homepage with:

1. **Clean, minimalist design** inspired by top-tier academic institutions
2. **Mobile-first responsive layout** that works on all devices
3. **Semantic HTML5** for accessibility and SEO
4. **Modern CSS3** with CSS Grid, Flexbox, and custom properties
5. **Organized publications** grouped by year with venue highlighting
6. **Professional presentation** befitting a research director

**Key improvements over old site:**
- Modern HTML5/CSS3 (replaces HTML 4.01 table layout)
- Responsive design (replaces fixed 860px width)
- Clean typography and spacing
- Visual hierarchy with proper sectioning
- Award badges for distinguished papers
- Better link organization with slides/talk links

