# 🚀 Space Exploration Quiz

A fun, interactive single-page web application for testing your knowledge about space exploration! This quiz features 10 engaging questions, smooth animations, and instant feedback.

## Features

- ✨ **10 space exploration questions** with instant feedback
- 🎨 **Beautiful UI** with smooth animations and transitions
- 🌙 **Dark mode support** with automatic detection
- ⌨️ **Keyboard friendly** - fully navigable with Tab and Enter
- 📱 **Responsive design** - works on desktop and mobile
- ⚡ **Zero dependencies** - pure HTML, CSS, and JavaScript
- 📦 **Single file app** - just one HTML file, no build step needed

## Quick Start

### Option 1: Open Locally
1. Clone or download this repository
2. Open `index.html` directly in your web browser
3. Start answering questions!

### Option 2: View Online
Visit the live version on [GitHub Pages](https://agapia3.github.io/space-quiz/) (when deployed)

## How to Use

1. Click on one of four answer options for each question
2. The app provides instant visual feedback:
   - ✅ Correct answers show a green pulse animation
   - ❌ Incorrect answers show a red shake animation
3. Your score updates automatically
4. After all 10 questions, you'll see your final score with an emoji-based reaction
5. Click "Try Again" to retake the quiz

## Development

Since this is a single-file application with no build step, development is straightforward:

1. Edit `index.html` directly
2. Refresh your browser to see changes
3. Test in different browsers to verify compatibility

### Project Structure

- **HTML** - Quiz layout, questions, and results screen
- **CSS** - Styling, animations, and responsive design
- **JavaScript** - Quiz logic, score tracking, and state management

### Adding Questions

To add new questions, edit the `quizData` array in the JavaScript section:

```javascript
quizData.push({
  question: "Your new question?",
  options: ["Option A", "Option B", "Option C", "Option D"],
  correct: 1  // Index of correct answer (0-based)
});
```

### Customizing Colors

Modify the CSS variables in the `:root` section to change the theme:

```css
:root {
  --bg-primary: #ffffff;
  --text-primary: #1a1a1a;
  --accent: #3b82f6;
  --success: #10b981;
  --error: #ef4444;
}
```

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

**Note:** ES6+ JavaScript is required. IE11 is not supported.

## Accessibility

- ✅ Full keyboard navigation support
- ✅ Semantic HTML structure
- ✅ WCAG AA color contrast compliance
- ✅ Dark mode support for reduced eye strain
- ✅ Focus indicators on all interactive elements

## Performance

- 📦 File size: ~16KB
- ⚡ Load time: Instant (no network requests)
- 🎯 60fps animations (CSS-based)
- 💾 Negligible memory footprint

## License

This project is open source and available under the MIT License.

## Feedback & Issues

Found a bug or have a feature suggestion? Please [open an issue](https://github.com/agapia3/space-quiz/issues) on GitHub!

---

**Happy quizzing!** 🌌
