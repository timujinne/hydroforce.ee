# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static HTML marketing website for Hydroforce, a company specializing in hydraulic motors and pumps. The site showcases product types (gear, planetary, axial-piston, and radial-piston motors), industry applications, technical specifications, and contact information.

**Technology Stack:**
- Pure HTML5 with external CSS (hydroforce-styles.css)
- No JavaScript frameworks or build tools
- No package manager or dependencies
- Responsive design using CSS media queries

## File Structure

The repository contains multiple HTML files representing different pages and design iterations:

### Production Pages:
- **`motors.html`** - Motors page **НОВАЯ ВЕРСИЯ** - использует внешний CSS файл hydroforce-styles.css
- **`Main.html`** - Main/Home page with hero, gallery showcase, quality sections
- **`HC.html`** - Hydraulic Cylinders page (BEST implementation example)
- **`Machining.html`** - Machining services page
- **`HPDieCasting.html`** - High-Pressure Die Casting page
- **`PM.html`** - Powder Metallurgy & Metal Injection Molding page

### Design System (v3.1):
- **`DESIGN_SYSTEM.html`** - **САМЫЙ ВАЖНЫЙ ФАЙЛ** - Унифицированная библиотека компонентов со всеми переиспользуемыми CSS классами и HTML паттернами
- **`hydroforce-styles.css`** - **ПРОИЗВОДСТВЕННЫЙ CSS** - Основной внешний файл стилей (обязательно для всех страниц)
- **`hydroforce-extended.css`** - **РАСШИРЕННЫЕ КОМПОНЕНТЫ** - Опциональные стили для специфических страниц (PM.html, HPDieCasting.html, gallery components)
- **`hydroforce-styles.min.css`** - Минифицированная production-версия основного CSS
- Всегда используйте DESIGN_SYSTEM.html как справочник при создании новых страниц

### Архивные версии (Motors section):
- **`V1.html`** - Alternative motors design with quote form
- **`V2.html`** - Motors design variant with gallery
- **`V3.html`** - Motors design with overlay hero

**ВАЖНО:** Новые страницы должны использовать внешний файл `hydroforce-styles.css` вместо встроенного CSS.

## Development Workflow

Since this is a static HTML project:

1. **Editing Files** - Open HTML files directly in a browser or use a local development server
2. **Testing Changes** - Simply refresh the browser after saving changes
3. **No Build Process** - Files are production-ready as-is
4. **Preview Options**:
   - Open files directly: `file:///path/to/index.html`
   - Use Python: `python -m http.server 8000`
   - Use VS Code Live Server extension

## CSS Architecture

The project uses a modular CSS approach with two external stylesheets:

### Core Stylesheet (Required)
**`hydroforce-styles.css`** - Base design system containing:
- CSS variables (colors, fonts, spacing, shadows)
- Typography system (H1-H5, paragraphs)
- Layout components (hero, grids, containers)
- Core UI elements (buttons, cards, sections)
- Responsive breakpoints
- All essential styles needed for standard pages

**Usage:** Include in every page:
```html
<link rel="stylesheet" href="hydroforce-styles.css">
```

### Extended Components (Optional)
**`hydroforce-extended.css`** - Specialized components for specific pages:
- Benefit boxes with colored backgrounds (PM.html, HPDieCasting.html)
- Why lists with centered styling (HPDieCasting.html)
- Gallery showcase layouts (Main.html, HC.html)
- Tech specs with advanced formatting
- Background image sections with fixed attachment

**Usage:** Include only when page needs these components:
```html
<link rel="stylesheet" href="hydroforce-styles.css">
<link rel="stylesheet" href="hydroforce-extended.css">
```

**Pages requiring extended.css:**
- PM.html (benefit boxes)
- HPDieCasting.html (benefit boxes, why lists)
- Main.html (gallery showcase)
- HC.html (dual-image gallery)

### Production Version
**`hydroforce-styles.min.css`** - Minified version of core stylesheet for production deployment with reduced file size.

### Legacy Pages
V1.html, V2.html, V3.html contain embedded CSS in `<style>` tags (archive versions, kept for reference).

## Design System

### Brand Colors
- **Primary Blue:** `#01577d` - Headings, buttons, brand elements
- **Accent Blue:** `#0a6a94` - Gradients, hover states
- **Accent Red:** `#bc3636` - Hover effects, call-to-action highlights
- **Neutral Gray:** `#2c3e50`, `#34495e`, `#5a6c7d` - Text and backgrounds
- **Light Gray:** `#f8f9fa`, `#e9ecef` - Section backgrounds

### Typography
- **Font Family:** 'Roboto', 'Arial', sans-serif
- **H1:** 3rem (3.5rem in motors.html), bold, primary blue
- **H2:** 2.5rem (2.8rem in motors.html), semi-bold, primary blue
- **H3:** 1.8rem, semi-bold
- **H4:** 1.4rem, medium weight
- **Body:** 1rem, line-height 1.6-1.7

### Responsive Breakpoints
- **Desktop:** Default (max-width: 1200px container)
- **Tablet:** `@media (max-width: 1024px)` - 2-column grids
- **Mobile:** `@media (max-width: 768px)` - Single column layouts
- **Small Mobile:** `@media (max-width: 480px)` - Reduced padding and font sizes

## Content Sections

**Note:** Content structure varies by page type. Below are standard sections for **Motors page** (motors.html, V1-V3.html):

1. **Hero Section** - Company introduction with stats and CTA buttons
2. **Products Section** - Four motor types (Gear, Planetary, Axial-Piston, Radial-Piston)
3. **Applications Section** - Six industry categories (Construction, Agriculture, Marine, Mining, Industrial, Municipal)
4. **Advantages Section** - Key benefits (torque, control, durability, versatility)
5. **Technical Specifications** - Performance ranges, operating conditions, mounting options
6. **CTA/Contact Section** - Contact information and action buttons

**Other pages have unique structures:**
- **HC.html** - Hero, dual-image gallery, application cards, quality section, specs
- **PM.html** - Hero, advantages, technology sections, applications, why PM/MIM, quality assurance
- **HPDieCasting.html** - Hero, benefits, why die casting, applications, tech specs
- **Machining.html** - Services-focused layout with capabilities showcase
- **Main.html** - Homepage with showcase gallery and quality highlights

### Hero Stats (Consistent Across Versions)
- 25+ Years of Expertise
- 500+ Motor Models
- 450 bar Max Pressure
- 24/7 Technical Support

### Technical Specifications (Standardized)
- Pressure: Up to 450 bar continuous
- Torque Output: 0.5 - 50,000 Nm
- Speed Range: 0.5 - 10,000 RPM
- Displacement: 8 - 8000 cc/rev
- Temperature: -40°C to +120°C
- Efficiency: Up to 95%

## External Dependencies

**Image Hosting:**
- Primary domain: `https://www.hydroforce.ee/wp-content/uploads/`
- Secondary domain: `https://bha.rs/wp-content/uploads/`

**Image Categories:**
- Product images (motors): `/2025/09/` directory
- Application backgrounds: `/2025/06/` directory
- Hero backgrounds: `/2025/09/motors-pumps-hero.webp`

**Note:** All images are externally hosted. Changes to image paths require updating URLs in the HTML files.

## Common Development Tasks

### Updating Content
- Edit text directly in HTML files
- Maintain semantic HTML structure
- Preserve accessibility attributes (alt text, aria labels)

### Modifying Styles
- **Modern pages** (index.html, PM.html, HC.html, etc.) use external CSS files:
  - `hydroforce-styles.css` - base styles (required)
  - `hydroforce-extended.css` - optional components (include when needed)
- **Archive pages** (V1.html, V2.html, V3.html) still use embedded `<style>` tags
- Always keep responsive breakpoints consistent when making changes
- Test changes across all breakpoints (Desktop → Tablet → Mobile)

### Adding New Sections
- Follow existing grid patterns: `display: grid; gap: 2rem;`
- Use consistent padding: `5rem 0` for sections (desktop), `3rem 0` (mobile)
- Apply section headers with `.section-header` class pattern

### Color Scheme Updates
- Primary brand colors are used consistently across buttons, headings, and accents
- Hover states typically darken or shift to accent red (#bc3636)
- Gradients use `linear-gradient(135deg, primary, accent)`

## Key Design Patterns

### Grid Layouts
- Products: 4 columns → 2 columns → 1 column (responsive)
- Applications: 3 columns → 2 columns → 1 column
- Specifications: 3 columns → 2 columns → 1 column

### Card Components
- Border radius: 12px - 16px
- Box shadow: `0 5px 20px rgba(0,0,0,0.08)` (default), `0 15px 35px rgba(0,0,0,0.15)` (hover)
- Hover effects: `translateY(-5px to -10px)` with increased shadow

### Buttons
- Primary: Blue gradient background, white text
- Secondary: Transparent with blue border, blue text
- Hover: Transform with `translateY(-2px)` and enhanced shadow
- Padding: 14-16px vertical, 28-32px horizontal

## DESIGN_SYSTEM.html - Unified Component Library

**MOST IMPORTANT:** Always use `DESIGN_SYSTEM.html` as the primary reference when creating new pages or components.

### What's Inside:
- **CSS Variables** - Minimalist color palette (2 corporate colors + neutrals), fonts, spacing, shadows
- **Typography System** - H1-H5 styles, paragraphs
- **Buttons** - Primary, secondary, CTA, rounded CTA variants
- **Hero Section** - Single standard: text on background image with dark overlay (no white/gradient boxes)
- **Cards** - Product cards, info cards, numbered cards, application cards
- **Grids** - 2, 3, 4 column layouts, auto-fit grids
- **Galleries** - Showcase gallery (1 large + 4 small), dual-image gallery, product gallery
- **Lists** - Tech specs, feature lists, why lists
- **Sections** - Industries, quality, CTA, benefits
- **Application Cards (v3.0)** - Cover image backgrounds for "Industries We Serve", red highlight stats

### Best Practices from Production Pages:

**From HC.html (BEST implementation):**
- Hero with text directly on dark overlay (background image required, no white boxes)
- Gallery with two images side-by-side
- Application cards with `object-fit: cover` for dramatic backgrounds
- Quality section on dark blue background with red bullet points
- Red highlight stats instead of blue for emphasis

**From HPDieCasting.html:**
- Benefit boxes with colored backgrounds (green, blue, yellow)
- Why list with centered text and borders
- Rounded white CTA buttons on colored backgrounds
- Tech specs with min-width for label alignment
- Background image sections with fixed attachment

### Creating New Pages:
1. Подключите внешний CSS: `<link rel="stylesheet" href="hydroforce-styles.css">`
2. Используйте готовые компоненты из DESIGN_SYSTEM.html (с примерами кода и живыми демо)
3. Reference `HC.html` для вдохновения по макету (лучшая структура)
4. Поддерживайте единообразие корпоративных цветов и отступов

### Структура motors.html (новая версия):
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <link rel="stylesheet" href="hydroforce-styles.css">
</head>
<body>
    <!-- Hero Section: .hero-overlay с фоновым изображением -->
    <!-- Products: .grid-4 с .product-card -->
    <!-- Applications: .grid-3 с .application-card (фоновые изображения) -->
    <!-- Advantages: .grid-4 с .card -->
    <!-- Specs: .grid-3 с .card и .tech-specs -->
    <!-- CTA: .cta-section -->
</body>
</html>
```

Страница использует классы из hydroforce-styles.css с некоторым дополнительным встроенным CSS для page-specific стилей (enhanced hero stats, enlarged product images).

## Version Differences (Motors Pages)

- **motors.html**: Most polished, comprehensive layout with enhanced hero section, page-specific styles for visual enhancements
- **V1.html**: Includes quote form, simplified design with purple gradient "Why Choose" section
- **V2.html**: Features gallery-style product showcase with image-heavy layout
- **V3.html**: Clean overlay design with background image hero section

Choose the appropriate version based on design requirements or use as reference for creating new variations.