# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Halo House is a single-page static website for an event planning and design business specializing in weddings. The site is built with vanilla HTML, CSS, and JavaScript with no build process or dependencies.

**Business Context:**
- Owners: Carly and Hayley (sisters who own Sorella 1881 wedding venue)
- Services: Full-service wedding planning and design
- Location: St. Catharines, ON
- Contact: halohouseevents@gmail.com, (905) 980-4855

## Architecture

**Single-File Structure:**
The entire website is contained in `halo-house.html` with embedded CSS and JavaScript. This is an intentional design choice for simplicity and portability.

**Styling Approach:**
- CSS custom properties for theming (`:root` variables)
- Mobile-first responsive design with breakpoints at 768px and 1024px
- Custom animations using CSS keyframes
- Intersection Observer API for scroll-based animations
- Smooth scroll navigation

**Key Design Elements:**
- Color palette: cream (#F5F1E8), dark (#2A2520), accent (#8B7355), light-accent (#C4B5A0)
- Typography: Cormorant Garamond (serif, decorative) + Montserrat (sans-serif, body)
- Video hero section with fallback
- Scroll-triggered section reveals

**Form Integration:**
The contact form uses EmailJS for email delivery without a backend server:
- Public Key: `8stJOBZD0GctfUJLy`
- Service ID: `service_ftrgl0r`
- Template ID: `template_azdid0t`

## Development Commands

**Local Development:**
```bash
# Open in browser directly (no build step required)
start halo-house.html
# or
open halo-house.html
```

**Testing:**
No automated tests. Manual testing required for:
- Video playback and fallback image
- Form submission via EmailJS
- Responsive breakpoints (768px, 1024px)
- Smooth scroll navigation
- Scroll animations on all sections

**Deployment:**
Static hosting only. No build process. Simply upload:
- `halo-house.html`
- `SORELLA.mp4`
- `aboutus.webp`
- `completesupport.PNG`
- `halo house transparent.png` (logo asset)
- `hh transparent.png` (logo asset)

## Important Implementation Details

**Video Hero Section:**
- Primary: SORELLA.mp4 (276MB - consider optimization)
- Fallback: SVG gradient placeholder embedded as data URI
- Video must autoplay, loop, and be muted for browser compatibility

**Navigation Behavior:**
- Fixed positioning with transparency overlay initially
- Transforms to solid cream background on scroll (>100px)
- Text color inverts from white to dark on scroll

**Section Animation System:**
All major sections (`.quote-section`, `.about-section`, `.services-section`, `.behind-section`, `.contact-section`) use Intersection Observer to trigger fade-in animations when 20% visible with 100px bottom margin.

**Image References:**
- `aboutus.webp` - About section background (line 235)
- `completesupport.PNG` - Services section image (line 320)
- Logo images are in root but not currently used in HTML

## Modification Guidelines

**When editing styles:**
- Use CSS custom properties defined in `:root` for colors
- Maintain the mobile-first approach (default styles, then media queries)
- Preserve animation timing and easing functions for brand consistency

**When editing content:**
- Section structure follows pattern: full-width sections with internal max-width containers
- Maintain semantic HTML structure for accessibility
- Keep font hierarchy: Cormorant Garamond for headings, Montserrat for body

**When adding features:**
- No npm/build tools - keep vanilla JavaScript
- Any new external dependencies should use CDN links
- Test video playback across browsers (Safari, Chrome, Firefox)

**EmailJS Configuration:**
If contact form stops working, verify EmailJS credentials are valid at https://dashboard.emailjs.com/
