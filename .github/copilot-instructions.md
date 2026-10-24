# Copilot Instructions for Space Quiz

## Project Overview

**Space Exploration Quiz** is a single-file, zero-dependency web application—a 10-question interactive quiz with animations, score tracking, and a results screen. The entire application (HTML + CSS + JavaScript) is contained in `index.html`.

### Key Characteristics
- **No build step** — Open `index.html` directly in a browser
- **No external dependencies** — Pure HTML/CSS/JavaScript
- **No test framework** — Manual testing via browser
- **Vanilla JavaScript** — ES6+ syntax (no frameworks)
- **Responsive design** — Centered narrow column (max 600px width)
- **Dark mode support** — CSS variables with `prefers-color-scheme` media query

---

## Architecture

### Single-File Structure

The application is fully self-contained in `index.html`:

1. **HTML (lines ~1–270)**
   - Header with title and subtitle
   - Progress section (question counter, score badge, progress bar)
   - Quiz content area (question + option buttons)
   - Results screen (emoji, score, message, restart button)

2. **CSS (lines ~7–265)**
   - Custom CSS variables for theming (light/dark mode)
   - Flexbox layout for centering and stacking
   - Animations: `slideDown`, `slideUp`, `fadeIn`, `pulse`, `shake`, `bounce`
   - Responsive sizing with `max-width: 600px` container
   - No CSS framework dependencies

3. **JavaScript (lines ~270–400)**
   - `quizData` array: 10 question objects with options and correct answer index
   - Quiz state: `currentQuestion`, `score`, `answered` flags
   - Core functions:
     - `initialize()` — Starts the quiz
     - `loadQuestion()` — Renders current question and options
     - `selectAnswer(index)` — Handles answer selection, animations, score
     - `updateProgress()` — Updates progress bar and question counter
     - `showResults()` — Displays results screen with emoji/message
     - `restartQuiz()` — Resets state for retake

---

## Development Workflow

### How to Test

1. **Open in Browser:**
   ```
   Open file:///C:/Users/agapi/Documents/space%20quiz/index.html in any modern browser
   ```

2. **Test Checklist:**
   - Click through all 10 questions
   - Verify score increments correctly
   - Check animations: green pulse (correct), red shake (incorrect)
   - Confirm results screen shows appropriate emoji and message
   - Test keyboard navigation (Tab to focus buttons, Enter to select)
   - Toggle dark mode in browser settings to verify theme switching
   - Click "Try Again" to verify reset

### No Build, Lint, or Test Commands

This project has no tooling. All changes are made directly to `index.html`. Validation is browser-based.

---

## Key Conventions

### CSS Architecture

- **CSS Variables** are the primary theming mechanism:
  - Light mode: `#ffffff` bg, `#1a1a1a` text
  - Dark mode: `#1a1a1a` bg, `#ffffff` text
  - Update `@media (prefers-color-scheme: dark)` to modify dark theme

- **Animation Timing:**
  - Feedback delay: `1200ms` (see `setTimeout` in `selectAnswer()`)
  - Hover transitions: `0.2s ease`
  - Progress bar: `0.4s cubic-bezier(0.34, 1.56, 0.64, 1)`
  - Answer animations: `0.5s ease` (pulse/shake)

- **Color Semantics:**
  - `--success` (`#10b981`) — Correct answers
  - `--error` (`#ef4444`) — Incorrect answers
  - `--accent` (`#3b82f6`) — Interactive elements, progress bar

### JavaScript Patterns

- **Question Data:**
  ```javascript
  {
    question: "Question text?",
    options: ["Option 1", "Option 2", "Option 3", "Option 4"],
    correct: 1  // Index of correct option (0-based)
  }
  ```

- **State Management:**
  - Answers locked during feedback: `answered` flag prevents double-clicks
  - Buttons disabled: `btn.disabled = true` during animation period
  - Smooth progression: `setTimeout(..., 1200)` before advancing to next question

- **Screen Toggling:**
  - Quiz: `.quiz-content.active` (display: block)
  - Results: `.results-screen.active` (display: block)
  - Only one screen visible at a time via class toggling

### Adding a New Question

1. Add an object to `quizData` array:
   ```javascript
   {
     question: "Your question here?",
     options: ["Wrong 1", "Correct", "Wrong 2", "Wrong 3"],
     correct: 1
   }
   ```

2. Update `totalQuestions` count in HTML if changing question count (line ~248):
   ```javascript
   document.getElementById('totalQuestions').textContent = quizData.length;
   ```
   *(This is automatic in current implementation)*

3. Test in browser to confirm progression and scoring.

### Modifying Results Messages

Emoji reactions and messages are hardcoded in `showResults()` function based on percentage:
- 100% → 🏆 "Perfect score!"
- 80–99% → ⭐ "Excellent!"
- 60–79% → 👍 "Good job!"
- 40–59% → 📚 "Not bad!"
- Below 40% → 🌌 "Keep exploring!"

Modify the corresponding conditions to change messaging or emoji.

### Font and Typography

- **Font family:** System font stack (`-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, ...`)
- **Body size:** `15px` (readable, meets accessibility standards)
- **Headings:** `32px` (title), `20px` (results title), `48px` (final score)

---

## Quick Reference

| Task | File | Location |
|------|------|----------|
| Add question | `index.html` | `quizData` array (line ~306) |
| Change colors | `index.html` | `:root` CSS variables (line ~18) |
| Modify animations | `index.html` | CSS `@keyframes` (lines ~210–260) |
| Edit feedback delay | `index.html` | `setTimeout` in `selectAnswer()` (line ~380) |
| Change result messages | `index.html` | `showResults()` function (line ~385) |
| Adjust layout width | `index.html` | `.container { max-width: 600px; }` (line ~53) |

---

## Browser Support

- **Modern browsers only:** Chrome, Firefox, Safari, Edge
- **ES6+ required:** Arrow functions, template literals, `const/let`
- **CSS features:** CSS Variables, Flexbox, Media Queries, Gradients
- **No IE11 support**

---

## Performance Notes

- **File size:** ~16KB (single HTML file)
- **Load time:** Instant (no network requests)
- **Animation performance:** 60fps (all via CSS `@keyframes`)
- **Memory:** Negligible (10 question objects in memory)

---

## Accessibility

- **Keyboard navigation:** All buttons focusable via Tab key
- **Focus states:** Buttons receive visual focus outline from browser
- **Color contrast:** WCAG AA compliant in both light and dark modes
- **Font size:** 15px body text exceeds minimum readability standards
- **Semantic HTML:** Proper button elements, no `<div>` role hacks

---

## Common Modifications

### Change Quiz Topic
Replace `quizData` array questions and update header subtitle (line ~241):
```javascript
<h1>🔬 Science Quiz</h1>
<p>Test your knowledge about science</p>
```

### Add Custom Styling
Insert new CSS rules before closing `</style>` tag. CSS variables will automatically adapt to dark mode.

### Adjust Animation Speed
Modify timing values:
- `1200ms` → feedback display duration
- `0.4s` → progress bar animation
- `0.5s` → pulse/shake animation duration

---

## Notes for Future Sessions

- This is a polished, production-ready single-file app
- No dependencies means changes are immediate (reload browser)
- Test any modifications by opening `index.html` in the browser
- Keep the `answered` flag logic to prevent multiple submissions during animation
- Maintain CSS variable structure for consistent theme support
