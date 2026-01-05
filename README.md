# Three Kings Gift Voucher

An interactive gift voucher web application for Three Kings Day (Epiphany), featuring a star-catching game that reveals a Michelin star restaurant voucher.

## Features

- **Interactive Star Catching Game**: Users must catch 3 falling stars by clicking or touching them
- **Beautiful Animations**: Smooth GSAP-powered animations for stars, envelope opening, and voucher reveal
- **Middle Eastern Theme**: Rich colors, ornate patterns, and elegant typography inspired by the Three Kings journey
- **Fully Accessible**: WCAG 2.2 Level AA compliant with:
  - Keyboard navigation support (Tab + Enter/Space to catch stars)
  - ARIA labels and live regions for screen readers
  - Focus indicators for interactive elements
  - Reduced motion support for users with motion sensitivity
- **Responsive Design**: Mobile-first approach that works on all devices
- **Touch Support**: Full touch event handling for mobile devices

## Tech Stack

- **Astro**: Static site generation
- **Tailwind CSS 4**: Modern utility-first styling with custom theme
- **GSAP**: Professional-grade animations
- **TypeScript**: Type-safe development

## Getting Started

### Install Dependencies

```bash
npm install
```

### Development

```bash
npm run dev
```

Visit `http://localhost:4321` to see the application.

### Build for Production

```bash
npm run build
```

The static files will be generated in the `dist/` directory.

### Preview Production Build

```bash
npm run preview
```

## Project Structure

```
src/
├── components/
│   ├── StarCatcher.astro    # Main game component
│   ├── Envelope.astro        # Envelope opening animation
│   └── VoucherCard.astro     # Final voucher display
├── layouts/
│   └── Layout.astro          # Base layout with fonts and meta tags
├── pages/
│   └── index.astro           # Entry point
└── styles/
    └── global.css            # Global styles and theme
```

## How It Works

1. **Page Load**: The application displays falling stars with a counter showing "0/3 Stars Caught"
2. **Star Catching**: Users click or touch falling stars to catch them
3. **Progress**: Each caught star increments the counter and removes the star with a scale animation
4. **Game Complete**: After catching 3 stars, the envelope appears
5. **Envelope Opening**: The envelope flap opens with a 3D rotation animation
6. **Voucher Reveal**: The voucher card appears with a scale and fade-in animation

## Accessibility Features

- All interactive stars are `<button>` elements with proper ARIA labels
- Keyboard navigation fully supported (Tab to focus, Enter/Space to activate)
- Screen reader announcements for caught stars using `aria-live` regions
- Focus indicators visible on all interactive elements
- Respects `prefers-reduced-motion` user preference
- High color contrast (4.5:1 minimum) for all text

## Customization

### Recipient Information

Edit the constants in `/src/components/VoucherCard.astro`:

```astro
const restaurantName = "Prodigi";
const recipientName = "Alex Cabrera Rastrilla";
```

### Color Theme

Modify the theme variables in `/src/styles/global.css`:

```css
@theme {
  --color-desert-sand: #f4e6d2;
  --color-golden: #d4af37;
  --color-royal-gold: #ffd700;
  /* ... more colors */
}
```

### Animation Duration

Adjust animation speeds in the component scripts:
- Star falling duration: `StarCatcher.astro` - `animateStar()` function
- Envelope opening: `Envelope.astro` - `openEnvelope()` function

## Browser Support

- Modern browsers (Chrome, Firefox, Safari, Edge)
- Mobile browsers (iOS Safari, Chrome Mobile)
- Requires JavaScript enabled
- Best viewed on screens 320px and wider

## License

Private project for personal use.
