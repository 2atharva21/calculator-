# Contributing to NEXUS Calculator

Thank you for your interest in contributing! We welcome contributions of all kinds.

---

## Table of Contents

1. [Code of Conduct](#code-of-conduct)
2. [How to Contribute](#how-to-contribute)
3. [Development Setup](#development-setup)
4. [Coding Guidelines](#coding-guidelines)
5. [Testing](#testing)
6. [Submitting Changes](#submitting-changes)
7. [FAQ](#faq)

---

## Code of Conduct

All contributors must follow our [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md). This includes:

- Being respectful and inclusive
- No harassment or discrimination
- Constructive feedback only
- Report violations to [Your Email]

---

## How to Contribute

### Option 1: Report Issues

Found a bug? Have a suggestion?

1. **Search First**
   - Check [existing issues](https://github.com/yourusername/nexus-calculator/issues)
   - Avoid creating duplicates

2. **Create Issue**
   - Click "New Issue"
   - Choose template: Bug or Feature
   - Fill in all fields
   - Include examples/screenshots

3. **Example Bug Report**
   ```markdown
   **Title:** Keyboard shortcut 'S' not toggling scientific mode
   
   **Browser:** Chrome 120.0
   **OS:** Windows 11
   **Steps to reproduce:**
   1. Open calculator
   2. Press 'S' key
   3. Scientific buttons don't appear
   
   **Expected:** Scientific mode toggles
   **Actual:** No response
   ```

---

### Option 2: Improve Documentation

Help make NEXUS easier to understand!

**What to improve:**
- Fix typos or grammar
- Clarify unclear explanations
- Add examples
- Translate documentation
- Add troubleshooting tips

**How to contribute:**
1. Find file to improve (README.md, DOCS.md, etc.)
2. Click edit icon (pencil)
3. Make changes
4. Create pull request
5. We'll review and merge!

---

### Option 3: Submit Code

Want to add features or fix bugs?

**What we accept:**
- ✅ Bug fixes with tests
- ✅ New features discussed first
- ✅ Performance improvements
- ✅ Accessibility enhancements
- ✅ Code quality improvements

**What we don't accept:**
- ❌ External dependencies (keep zero-dependency)
- ❌ Breaking changes without discussion
- ❌ Undocumented changes
- ❌ Features without tests

---

## Development Setup

### Prerequisites

- Git
- Code editor (VS Code recommended)
- Web browser
- 10 minutes of free time

### Steps

#### 1. Fork Repository

```bash
# Visit https://github.com/yourusername/nexus-calculator
# Click "Fork" button (top right)
# This creates YOUR copy
```

#### 2. Clone Your Fork

```bash
git clone https://github.com/YOUR_USERNAME/nexus-calculator.git
cd nexus-calculator
```

#### 3. Create Feature Branch

```bash
# Never commit to main!
git checkout -b feature/awesome-feature
# OR for bug fixes
git checkout -b fix/button-not-working
```

#### 4. Open in Editor

```bash
# VS Code
code .

# Other editors: just open the folder
```

#### 5. Test Your Changes

```bash
# Open index.html in browser
# Test all functionality
# Test on mobile (DevTools device emulation)
```

---

## Coding Guidelines

### JavaScript Style

```javascript
// ✅ DO: Clear, meaningful names
class CalculatorLogic {
    constructor() {
        this.displayValue = '0';
        this.previousValue = null;
        this.operation = null;
    }
    
    append(digit) {
        // Handle decimal point logic
        if (digit === '.' && this.displayValue.includes('.')) {
            return; // Prevent multiple decimals
        }
        this.displayValue += digit;
    }
}

// ❌ DON'T: Cryptic, unclear code
class Calc {
    constructor() {
        this.dv = '0'; // Hard to understand
        this.pv = null;
        this.op = null;
    }
    
    a(d) { // "a" = what?
        this.dv += d;
    }
}
```

### Comments & Documentation

```javascript
// ✅ DO: Explain WHY, not WHAT
// Prevent division by zero error - show friendly message
if (divisor === 0) {
    this.displayValue = 'ERROR';
    this.errorState = true;
    return;
}

// ✅ DO: Document complex logic
// Convert degrees to radians for trigonometric functions
// because Math.sin() expects radians, not degrees
const radians = angle * (Math.PI / 180);

// ❌ DON'T: State the obvious
// Set operation to add
this.operation = '+';

// ❌ DON'T: Comment bad code - fix it instead
if ((a===b&&c!=d)||e==f&&(g<h)) { // This is confusing!
```

### CSS Best Practices

```css
/* ✅ DO: Use CSS variables for theming */
:root {
    --operator-bg: #FF9500;
    --operator-hover: #FFB84D;
}

/* ✅ DO: Animations only use transform & opacity */
.btn:active {
    transform: scale(0.95);      /* Fast, GPU-accelerated */
    opacity: 0.9;
}

/* ❌ DON'T: Animate other properties */
.btn:active {
    width: 90px;                 /* Slow, CPU-heavy */
    box-shadow: 0 0 20px red;    /* Causes reflow */
}
```

### HTML

```html
<!-- ✅ DO: Semantic markup with ARIA labels -->
<button 
    class="btn btn-operator" 
    data-operator="+" 
    aria-label="Add"
    title="Addition (+)">
    +
</button>

<!-- ❌ DON'T: Generic divs without accessibility -->
<div onclick="handleAddition()">+</div>
```

---

## Testing

### Browser Compatibility

Test your changes in:

- [ ] Chrome (latest)
- [ ] Firefox (latest)
- [ ] Safari (latest)
- [ ] Edge (latest)

### Mobile Testing

```
- [ ] Android (Chrome)
- [ ] iOS (Safari)
- [ ] Portrait orientation
- [ ] Landscape orientation
- [ ] Touch input
- [ ] Landscape orientation
```

### Feature Testing

```
Before submitting code, verify:

Standard Mode:
- [ ] Basic operations (+ − × ÷)
- [ ] Decimal point works
- [ ] Clear button resets
- [ ] Sign toggle works
- [ ] Keyboard input works

Scientific Mode:  
- [ ] Toggle SCI button shows/hides functions
- [ ] Trigonometric functions work
- [ ] Memory functions work
- [ ] History displays correctly
- [ ] Angle mode toggle works

UI:
- [ ] Theme toggle cycles all themes
- [ ] Animations are smooth
- [ ] Display updates correctly
- [ ] No console errors
- [ ] Responsive on all sizes
```

### Accessibility Testing

```
- [ ] Tab key navigates all buttons
- [ ] Focus indicators visible
- [ ] Screen reader friendly (text labels)
- [ ] Sufficient color contrast
- [ ] Respects prefers-reduced-motion
```

---

## Submitting Changes

### Step 1: Commit Your Changes

```bash
# Stage changes
git add .

# Commit with descriptive message
git commit -m "Add factorial function to scientific mode

This allows users to calculate n! directly.
- Added factorial() method to CalculatorLogic
- Added ! button to scientific panel
- Button triggers factorial calculation
- Tested on mobile and desktop"
```

**Commit message tips:**
- First line: Short summary (50 chars max)
- Blank line
- Detailed explanation (what, why, how)
- Reference issues: "Fixes #123"

### Step 2: Push to Your Fork

```bash
git push origin feature/awesome-feature
```

### Step 3: Create Pull Request

1. Visit your fork on GitHub
2. Click "Compare & pull request"
3. Fill in title and description
4. Submit PR

### Step 4: PR Template

```markdown
## Description
Brief description of what changed and why.

## Related Issues
Fixes #123
Related to #456

## Changes Made
- Added new function X
- Fixed bug in Y
- Updated documentation

## Testing
- [x] Tested on Chrome
- [x] Tested on Mobile
- [x] Tested scientific mode
- [x] No console errors

## Screenshots (if applicable)
[Paste screenshots here]
```

---

## Code Review Process

1. **We review your PR**
   - Verify tests pass
   - Check code style
   - Review logic

2. **We may request changes**
   - Update your code
   - Push new commits
   - We re-review

3. **PR approved!**
   - We merge to main
   - Your changes go live
   - You're credited

---

## FAQ

### Q: Where should I report bugs?

A: Create an [issue on GitHub](https://github.com/yourusername/nexus-calculator/issues) with:
- Browser/OS version
- Steps to reproduce
- Expected vs actual behavior
- Screenshots if helpful

---

### Q: How long do reviews take?

A: Usually 2-7 days depending on complexity. We review in order received.

---

### Q: Can I add external libraries?

A: No, NEXUS must stay at zero dependencies for performance and simplicity. Suggest alternatives if needed.

---

### Q: What if my PR gets rejected?

A: No problem! We can:
1. Discuss improvements needed
2. Suggest changes
3. Submit new version
4. All feedback is constructive!

---

### Q: Do I get paid for contributions?

A: NEXUS is open-source volunteer project. Recognition and portfolio building are rewards!

---

### Q: Can I translate the app?

A: Absolutely! Create README or DOCS in your language. Currently we support English, so translations welcome!

---

## Recognition

Contributors are recognized in:
- README.md contributors section
- GitHub contributors graph
- Release notes

---

## Questions?

- 📧 Email: [Your Email]
- 💬 [GitHub Discussions](https://github.com/yourusername/nexus-calculator/discussions)
- 🐛 [GitHub Issues](https://github.com/yourusername/nexus-calculator/issues)

---

## Thank You! 

Your contributions make NEXUS better for everyone. We appreciate your time and effort! 🎉
  // Batch updates
  element.classList.remove('old');
  element.classList.add('new');
  ```

- ✅ **DO**: Keep animations under 250ms
- ✅ **DO**: Test on low-end phones (Galaxy J2, Moto E, etc.)
- ✅ **DO**: Verify 60fps with Chrome DevTools (Rendering tab)

### **Accessibility**

- Add ARIA labels to interactive elements
- Ensure keyboard navigation works
- Test with screen readers
- Maintain color contrast ratios (WCAG AA)
- Support reduced motion preference

---

## 🔄 Contribution Workflow

### **Step 1: Fork & Clone**
```bash
git clone https://github.com/YOUR_USERNAME/CALCORA.git
cd CALCORA
```

### **Step 2: Create Feature Branch**
```bash
git checkout -b feature/descriptive-name
```

Branch naming convention:
- `feature/add-xyz` - New feature
- `fix/issue-description` - Bug fix
- `docs/update-readme` - Documentation
- `refactor/improve-xyz` - Code improvement

### **Step 3: Make Changes**
- Edit `index.html` (contains all HTML, CSS, JS)
- Make focused, atomic commits
- Test thoroughly
- Verify no console errors

### **Step 4: Commit Properly**
```bash
git add .
git commit -m "brief description of changes"
```

Commit message guidelines:
- First line: clear, short summary (50 chars max)
- Leave blank line
- Body: explain WHAT and WHY (not HOW)

**Examples**:
```
✅ good
"Add scientific mode with trigonometric functions"

✅ good  
"Fix divide by zero error handling and add validation"

❌ bad
"Updated code"

❌ bad
"fixed stuff"
```

### **Step 5: Push & Create Pull Request**
```bash
git push origin feature/descriptive-name
```

1. Go to GitHub and create Pull Request
2. Fill out PR template completely
3. Link related issues
4. Wait for review

### **Step 6: Address Feedback**
- Review comments carefully
- Make requested changes
- Test thoroughly again
- Push updates (no force push)

### **Step 7: Merge**
Once approved, project maintainers will merge your PR. You're now a CALCORA contributor! 🎉

---

## 📂 Project Structure

```
index.html          # Main application file (~35KB, all-in-one)
├── <head>          # Meta, styles (no external dependencies)
├── <body>
│   ├── Background  # Animated gradient orbs
│   ├── Header      # App name, controls
│   ├── Calculator  # Main UI with buttons/display
│   └── <script>    # Lightweight JavaScript classes
│       ├── SoundEngine     # Web Audio API for sound
│       ├── AnimationEngine # CSS-based animations
│       ├── CalculatorLogic # Math operations
│       └── CalculatorApp   # Main app controller

README.md           # Full project documentation
INSTALLATION.md     # Setup instructions & performance details
CONTRIBUTING.md     # This file
LICENSE             # MIT License
DOCS.md             # Documentation index
```

**Zero Dependencies**: No CDN libraries - everything is native HTML/CSS/JS

---

## 🎯 Areas Looking for Contribution

### **High Priority**
- [ ] Unit and integration tests
- [ ] e2e testing setup
- [ ] Internationalization (i18n)
- [ ] PWA support

### **Medium Priority**
- [ ] Advanced math functions
- [ ] Expression parser
- [ ] Performance optimizations
- [ ] Additional themes

### **Lower Priority**
- [ ] Voice input
- [ ] Gesture support
- [ ] Custom button layouts
- [ ] Plugin system

---

## 🧪 Testing Before Submission

```bash
# Test basic operations
5 + 3 = 8          # Addition
10 - 4 = 6         # Subtraction
3 * 4 = 12         # Multiplication
15 / 3 = 5         # Division
10 % 3 = 1         # Modulo

# Test edge cases
0 / 0 = 0          # Division by zero
0.1 + 0.2 = 0.3    # Floating point
999999999 + 1      # Large numbers
-5 * -2 = 10       # Negatives

# Test UI/UX
Click all buttons - smooth animations
Type on keyboard - instant response
Toggle sound - audio plays
Toggle theme - colors change
Open history - slides smoothly
Test mobile view - responsive
```

---

## 💬 Communication

### **Asking Questions**
- Use [GitHub Discussions](https://github.com/yourusername/CALCORA/discussions)
- Be specific and provide context
- Search closed discussions first

### **Reporting Issues**
- Use [GitHub Issues](https://github.com/yourusername/CALCORA/issues)
- Search existing issues first
- Use issue templates provided

### **Getting Help**
- Review existing PRs and comments
- Check closed issues for solutions
- Ask in Discussions for guidance

---

## 📋 Pull Request Checklist

Before submitting your PR, ensure:

- [ ] Code follows project style guide
- [ ] Comments added for complex logic
- [ ] Tested on mobile and desktop
- [ ] No console errors or warnings
- [ ] Performance not degraded
- [ ] Accessibility maintained
- [ ] Updated README if needed
- [ ] Commit messages are clear
- [ ] Linked related issues
- [ ] No breaking changes

---

## 🏆 Recognition

Contributors are recognized in:
- README.md contributors section
- GitHub contributors page
- Release notes for major contributions

---

## ❓ FAQ

**Q: Can I work on an existing issue?**
A: Yes! Comment on the issue first to claim it.

**Q: Do I need to sign a CLA?**
A: No, we use MIT license which is very permissive.

**Q: How long does review take?**
A: Usually 2-7 days depending on complexity.

**Q: Can I submit multiple PRs?**
A: Yes! Smaller, focused PRs are easier to review.

**Q: What if my PR gets rejected?**
A: No problem! We'll explain why and suggest improvements.

**Q: Can I add external dependencies?**
A: Not for core functionality. We keep this lightweight.

---

## 🚀 Getting Started

1. Read this guide thoroughly
2. Look at existing [Issues](https://github.com/yourusername/CALCORA/issues)
3. Find something you'd like to work on
4. Comment on the issue to say you'll work on it
5. Fork and create your branch
6. Make changes and test thoroughly
7. Create a Pull Request
8. Wait for review and respond to feedback

---

## 📚 Useful Resources

- [GitHub Docs - Contributing](https://docs.github.com/en/get-started/quickstart/contributing-to-projects)
- [MDN Web Audio API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API)
- [GSAP Documentation](https://gsap.com/docs/)
- [Tailwind CSS Guide](https://tailwindcss.com/docs)
- [JavaScript Best Practices](https://google.github.io/styleguide/jsguide.html)

---

## ✨ Thank You!

Thank you for considering contributing to CALCORA! Your effort helps make this project better for everyone.

Happy coding! 🎉

---

**Questions?** Open an issue or discussion anytime!
