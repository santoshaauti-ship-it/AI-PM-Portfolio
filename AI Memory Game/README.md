# Memory Game

A responsive and accessible Memory (Concentration) card game built with HTML, CSS, and JavaScript. Features a dark theme toggle and comprehensive product documentation.

## Features

- 4x4 and 6x6 grid options
- **Dark Theme Toggle** - Switch between light and dark themes with persistence
- Smooth card flip animations with 3D effects
- Timer and moves counter with star rating system
- Local storage for best scores and theme preferences
- Full keyboard controls for accessibility (WCAG AA compliant)
- Responsive design for all devices
- No external dependencies

## How to Play

1. Open `memory-game.html` in a web browser
2. Click or use keyboard (Tab + Enter/Space) to flip cards
3. Find matching pairs to win
4. Try to complete the game with as few moves as possible
5. Switch between 4x4 and 6x6 grids using the buttons
6. **Toggle between light and dark themes** using the sun/moon button in the controls panel

## Dark Theme Feature

The game includes a sophisticated dark theme system:

- **Theme Toggle Button**: Sun (☀️) / Moon (🌙) icon in the controls panel
- **Persistent Preferences**: Your theme choice is saved and restored on page reload
- **Smooth Transitions**: 0.3s animated transitions between themes
- **Complete Coverage**: All UI elements (cards, controls, modals, scores) support both themes
- **Accessibility**: Maintains WCAG AA contrast ratios in both light and dark modes

## Technical Details

- Pure HTML, CSS, and JavaScript implementation
- CSS Custom Properties for dynamic theming
- localStorage for theme persistence and high scores
- No external libraries or dependencies
- Fully responsive design using CSS Grid and Flexbox
- Accessible with ARIA attributes and keyboard controls
- Cross-browser compatible (Chrome, Firefox, Safari, Edge)

## Project Documentation

This project includes comprehensive product documentation:

### Product Requirements Documents (PRDs)
- **[PRD.md](PRD.md)** - Complete product requirements for the Memory Game
- **[prd-darktheme.md](prd-darktheme.md)** - Detailed PRD for the dark theme toggle feature
- **[PRD-Skill.md](PRD-Skill.md)** - Standardized PRD writing guide and template

### Implementation Documentation
- **[IMPLEMENTATION-SUMMARY.md](IMPLEMENTATION-SUMMARY.md)** - Complete code changes summary for dark theme implementation

## Development

1. Clone the repository
2. Open `memory-game.html` in a web browser
3. Or serve using a local HTTP server:
   ```bash
   python3 -m http.server 8000
   ```
4. Visit `http://localhost:8000/memory-game.html`

## Architecture

### Theme System
```javascript
// CSS Custom Properties for theming
:root {
  --primary-color: #2196f3;
  --background-color: #f5f5f5;
  // ... light theme variables
}

[data-theme="dark"] {
  --primary-color: #64b5f6;
  --background-color: #121212;
  // ... dark theme overrides
}
```

### Theme Manager
```javascript
const themeManager = {
  getTheme() { /* retrieve from localStorage */ },
  setTheme(theme) { /* apply theme and save */ },
  toggleTheme() { /* switch between themes */ },
  init() { /* initialize on page load */ }
};
```

## Browser Support

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+
- Mobile browsers (iOS Safari, Chrome Mobile)

## Contributing

This project includes a comprehensive PRD writing guide (`PRD-Skill.md`) for maintaining consistent documentation standards. When proposing new features:

1. Create a PRD following the template in `PRD-Skill.md`
2. Include user stories, acceptance criteria, and technical specifications
3. Ensure accessibility and performance requirements are met
4. Test across supported browsers and devices

## License

This project is open source and available under the MIT License.