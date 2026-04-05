# Contributing to CALCORA

Thank you for your interest in contributing to CALCORA! We welcome contributions of all kinds - bug reports, feature requests, documentation improvements, and code contributions.

## 📋 Code of Conduct

Please note that this project is released with a [Contributor Code of Conduct](CODE_OF_CONDUCT.md). By participating in this project you agree to abide by its terms.

---

## 🚀 Ways You Can Contribute

### **1. Report Bugs** 🐛
Found a bug? Help us fix it!

1. Check existing [Issues](https://github.com/yourusername/CALCORA/issues) first
2. Provide a clear description with:
   - Browser and OS version
   - Steps to reproduce
   - Expected vs actual behavior
   - Screenshots if possible
3. Use the bug report template

### **2. Suggest Features** 💡
Have an idea? We'd love to hear it!

1. Check [Discussions](https://github.com/yourusername/CALCORA/discussions) first
2. Describe the use case and benefits
3. Provide examples if possible
4. Use the feature request template

### **3. Improve Documentation** 📚
Help us document CALCORA better!

- Fix typos or unclear explanations
- Add examples or tutorials
- Translate documentation
- Improve code comments

### **4. Submit Code** 💻
Ready to code? Let's make CALCORA better together!

---

## 🔧 Setting Up Development Environment

### **Prerequisites**
- Git
- A code editor (VS Code, Sublime, etc.)
- A modern web browser
- Node.js (optional, for advanced development)

### **Local Setup**

```bash
# 1. Fork the repository on GitHub
# 2. Clone your fork
git clone https://github.com/YOUR_USERNAME/CALCORA.git
cd CALCORA

# 3. Create a feature branch
git checkout -b feature/your-feature-name

# 4. Open in your browser
open index.html

# 5. Make your changes and test
```

---

## 📝 Development Guidelines

### **Code Style**

```javascript
// ✅ DO: Use ES6+ syntax, meaningful names, clear structure
class CalculatorLogic {
    constructor() {
        this.currentValue = '0';
        this.operation = null;
    }
    
    calculate() {
        // Clear logic with comments
    }
}

// ❌ DON'T: Avoid var, use short cryptic names, complex nesting
var cv = '0', o = null;
```

### **Comments & Documentation**

```javascript
// ✅ DO: Explain WHY, not WHAT
// Prevent duplicate operators from breaking calculation chain
if (this.operation && !this.shouldResetDisplay) {
    this.calculate();
}

// ❌ DON'T: State the obvious
// Set operation
this.operation = op;
```

### **Testing Checklist**

Before submitting, test on:
- [ ] Desktop Chrome
- [ ] Desktop Firefox
- [ ] Mobile Chrome
- [ ] Mobile Safari (iOS)
- [ ] Dark and light modes
- [ ] Sound ON and OFF
- [ ] Keyboard input
- [ ] Touch input
- [ ] Landscape and portrait orientations

### **Performance Considerations**

- Use CSS transforms and opacity for animations (GPU-accelerated)
- Minimize DOM manipulation
- Batch style updates
- Avoid layout thrashing
- Use requestAnimationFrame for custom animations

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
index.html          # Main application file
├── <head>          # Meta, Tailwind, GSAP, styles
├── <body>
│   ├── animated-bg # Gradient background
│   ├── Header      # App name, controls
│   ├── Calculator  # Main UI with buttons/display
│   └── <script>    # All JavaScript classes
│       ├── SoundEngine     # Web Audio API
│       ├── AnimationEngine # GSAP animations
│       ├── CalculatorLogic # Math operations
│       ├── ThemeManager    # Dark/light theme
│       └── CalculatorApp   # Main app class

README.md           # Documentation
LICENSE             # MIT License
CONTRIBUTING.md     # This file
```

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
