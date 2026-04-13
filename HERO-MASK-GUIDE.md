# Hero Mask Reveal Animation - Implementation Guide

## Overview
Premium editorial scroll-driven animation that creates a luxury "reflection illusion" effect using SVG text masking.

## How It Works

### Visual Effect
1. **Base Layer**: Full-screen background image (slightly faded during scroll)
2. **White Overlay**: Fades in from 0% to configurable opacity (default 80%)
3. **SVG Mask Layer**: "DROP EDITION" text reveals a sharp, high-contrast version of the same image
4. **Parallax**: Masked image moves vertically for depth

### Technical Implementation
- **Vanilla JavaScript** with `requestAnimationFrame` for 60fps performance
- **CSS Masking** using SVG files (`logo.svg` for desktop, `logo-s.svg` for mobile)
- **Scroll-driven** animation with configurable distance (default 300vh)
- **Responsive** with automatic SVG switching at 768px breakpoint

## Required Assets

### SVG Files (Already Added)
- `assets/logo.svg` - Desktop version of "DROP EDITION" text
- `assets/logo-s.svg` - Mobile version (optimized for smaller screens)

### Background Image
Upload via theme editor or use default `hero-banner.jpg`

## Theme Editor Settings

### Image
- **Background image**: Same image used for both layers
- Info: Masked version automatically enhanced with CSS filters

### Animation Settings

1. **Scroll distance** (200-500vh, default: 300vh)
   - Controls how long the animation takes to complete
   - Higher = slower, more dramatic reveal

2. **White overlay opacity** (0-100%, default: 80%)
   - Maximum opacity of the white fade
   - Creates the "faded background" effect

3. **Mask start size** (50-100%, default: 80%)
   - Initial size of the SVG text mask
   - Smaller = more dramatic growth

4. **Mask end size** (100-150%, default: 110%)
   - Final size of the SVG text mask at scroll completion
   - Larger = more immersive final state

5. **Parallax effect** (0-50%, default: 20%)
   - Vertical movement of masked image
   - Creates depth and motion

## Performance Optimizations

✅ **RequestAnimationFrame** - Smooth 60fps animations
✅ **Passive scroll listeners** - No scroll blocking
✅ **will-change CSS** - GPU acceleration
✅ **Progress throttling** - Skips redundant updates
✅ **Eager loading** - Hero images load immediately

## Browser Support

- ✅ Chrome/Edge (full support)
- ✅ Safari (full support with -webkit- prefixes)
- ✅ Firefox (full support)
- ✅ Mobile browsers (responsive SVG switching)

## Customization Tips

### Adjust Animation Speed
Increase `scroll_height` for slower, more cinematic reveal

### Change Overlay Color
Modify `.hero-overlay` background-color in CSS (currently white)

### Enhance Masked Image
Adjust filters on `.hero-mask__image`:
```css
filter: contrast(1.15) saturate(1.1) brightness(1.05);
```

### Different SVG Masks
Replace `logo.svg` and `logo-s.svg` with your own SVG text designs

## Usage in Templates

Add to any template JSON:
```json
{
  "sections": {
    "hero": {
      "type": "hero-banner",
      "settings": {
        "scroll_height": 300,
        "overlay_opacity": 80,
        "mask_start_size": 80,
        "mask_end_size": 110,
        "parallax_amount": 20
      }
    }
  },
  "order": ["hero"]
}
```

## Translation Keys

All labels use the `t:sections.hero_mask.*` namespace:
- `name` - Section name in editor
- `image` - Image picker label
- `animation_settings` - Settings header
- `scroll_height` - Scroll distance label
- `overlay_opacity` - Overlay opacity label
- `mask_start_size` - Start size label
- `mask_end_size` - End size label
- `parallax_amount` - Parallax label

## Troubleshooting

**Mask not visible?**
- Verify `logo.svg` and `logo-s.svg` exist in assets folder
- Check browser console for 404 errors

**Animation too fast/slow?**
- Adjust `scroll_height` setting in theme editor

**Overlay too strong?**
- Reduce `overlay_opacity` setting

**No parallax effect?**
- Increase `parallax_amount` setting
