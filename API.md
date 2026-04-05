# API Reference

Complete API documentation for integrating and extending NEXUS Calculator.

---

## Table of Contents

1. [CalculatorLogic API](#calculatorlogic-api)
2. [CalculatorApp API](#calculatorapp-api)
3. [Events & Callbacks](#events--callbacks)
4. [Data Structures](#data-structures)
5. [Examples](#examples)
6. [Troubleshooting](#troubleshooting)

---

## CalculatorLogic API

The core calculation engine. Handles all math operations and state management.

### Constructor

```javascript
const logic = new CalculatorLogic();
```

**Properties:**
```javascript
logic.displayValue        // Current display value (string)
logic.previousValue       // First operand (number)
logic.operation          // Current operator (string)
logic.waitingForNewValue // Is next digit new number? (boolean)
logic.history            // Array of calculations
logic.errorState         // Is there an error? (boolean)
logic.memory             // Memory value (number)
logic.angleMode          // 'deg' or 'rad'
logic.scientificMode     // Is scientific mode on? (boolean)
```

---

### Basic Operations

#### `append(value)`

Add a digit or decimal to the display.

```javascript
logic.append('5');          // Display: "5"
logic.append('3');          // Display: "53"
logic.append('.');          // Display: "53."
```

**Parameters:**
- `value` (string) - Digit or '.'

**Returns:** `string` - Updated display value

---

#### `setOperation(operator)`

Set the current operation.

```javascript
logic.append('5');
logic.setOperation('+');    // 5 + _
logic.append('3');
logic.calculate();          // Result: 8
```

**Parameters:**
- `operator` (string) - One of: `+`, `−`, `*`, `/`, `%`, `^`

**Returns:** `string` - Updated display

---

#### `calculate()`

Perform the calculation.

```javascript
logic.append('10');
logic.setOperation('+');
logic.append('5');
const result = logic.calculate();  // Returns: "15"
```

**Returns:** `string` - Calculation result

---

#### `clear()`

Reset calculator to initial state.

```javascript
logic.clear();
// All values reset to defaults
```

**Resets:**
- Display to "0"
- Previous value to null
- Operation to null
- Error state cleared

---

#### `addDecimal()`

Add decimal point if not already present.

```javascript
logic.append('5');
logic.addDecimal();        // Display: "5."
logic.addDecimal();        // No change (already has .)
```

**Returns:** `string` - Updated display

---

#### `backspace()`

Toggle number sign (positive/negative).

```javascript
logic.append('5');
logic.backspace();         // Display: "-5"
logic.backspace();         // Display: "5"
```

**Returns:** `string` - Updated display

---

### Scientific Functions

#### Trigonometric

```javascript
// Sine
logic.displayValue = '30';          // Set angle
logic.sine();                       // Calculate sin(30°)

// Cosine
logic.cosine();                     // Calculate cos(angle)

// Tangent
logic.tangent();                    // Calculate tan(angle)
```

**Returns:** `string` - Calculation result

**Note:** Angle mode affects input interpretation

---

#### Exponential & Logarithmic

```javascript
// Square root
logic.displayValue = '16';
logic.sqrt();                       // Result: "4"

// Square
logic.displayValue = '5';
logic.square();                     // Result: "25"

// Logarithm (base 10)
logic.displayValue = '100';
logic.logarithm();                  // Result: "2"

// Natural logarithm
logic.displayValue = '2.718';
logic.naturalLog();                 // Result: "1"

// e to the power
logic.displayValue = '2';
logic.exponential();                // Result: "7.389"
```

**Returns:** `string` - Calculation result

---

#### Other Functions

```javascript
// Square reciprocal (1/x)
logic.displayValue = '5';
logic.reciprocal();                 // Result: "0.2"

// Factorial (n!)
logic.displayValue = '5';
logic.factorial();                  // Result: "120"

// Get pi
logic.pi();                         // Display: "3.14159..."

// Get Euler's number
logic.euler();                      // Display: "2.71828..."

// Power (base ^ exponent)
logic.power(3);                     // Result: base^3
```

**Returns:** `string` - Result or updated display

---

### Memory Functions

```javascript
// Add to memory
logic.displayValue = '100';
logic.memoryAdd();                  // Memory: 100

// Subtract from memory
logic.displayValue = '30';
logic.memorySubtract();             // Memory: 70

// Recall memory
logic.memoryRecall();               // Display: "70"

// Clear memory
logic.memoryClear();                // Memory: 0

// Get memory value
const memValue = logic.getMemoryValue();  // Returns: 70
```

**Returns:** `string` - Updated display or result

---

### History Management

```javascript
// Get all history
const history = logic.getHistory();
// Returns: ["5 + 3 = 8", "10 * 2 = 20", ...]

// History automatically added with calculations
logic.displayValue = '5';
logic.setOperation('+');
logic.append('3');
logic.calculate();
// History now includes: "5 + 3 = 8"
```

**Returns:** `string[]` - Array of calculation strings

---

### Settings

```javascript
// Toggle angle mode
const mode = logic.toggleAngleMode();  // Returns: "rad" or "deg"

// Check current mode
if (logic.angleMode === 'deg') {
    // Use degrees
}
```

**Returns:** `string` - New angle mode

---

## CalculatorApp API

Main application controller. Manages UI, events, and themes.

### Constructor

```javascript
const app = new CalculatorApp();
```

**Auto-executes:**
- Event listener setup
- Theme loading
- Display update

---

### Method Reference

#### `setupThemeToggle()`

Initialize theme switching system.

```javascript
// Automatically called on init
// Cycles through: dark → light → ocean → sunset → forest
```

---

#### `applyTheme(themeName)`

Apply a specific theme.

```javascript
app.applyTheme('dark');             // Dark theme
app.applyTheme('ocean');            // Ocean theme
app.applyTheme('sunset');           // Sunset theme
```

**Parameters:**
- `themeName` (string) - One of: `dark`, `light`, `ocean`, `sunset`, `forest`

**Saves to:** `localStorage` automatically

---

#### `toggleScientificMode()`

Show/hide scientific function buttons.

```javascript
app.toggleScientificMode();         // Toggle on/off
```

**Shows:**
- Trigonometric functions
- Logarithmic functions
- Memory functions
- Constants and special operations

---

#### `updateDisplay()`

Refresh the display with current value.

```javascript
logic.append('5');
app.updateDisplay();                // Display updates immediately
```

Automatically called after most operations.

---

#### `updateMemoryDisplay()`

Refresh memory indicator.

```javascript
logic.memoryAdd();
app.updateMemoryDisplay();          // Shows "M: 5" if memory has value
```

---

### Properties

```javascript
app.logic                           // CalculatorLogic instance
app.scientificMode                  // Is scientific mode active? (boolean)
```

---

## Events & Callbacks

### Button Click Events

All buttons automatically wire to calculator logic:

```html
<!-- Number buttons -->
<button data-number="5">5</button>
<!-- On click: logic.append('5'), app.updateDisplay() -->

<!-- Operator buttons -->
<button data-operator="+">+</button>
<!-- On click: logic.setOperation('+'), app.updateDisplay() -->

<!-- Action buttons -->
<button data-action="equals">=</button>
<!-- On click: logic.calculate(), app.updateDisplay() -->

<!-- Scientific buttons -->
<button data-scientific="sqrt">√</button>
<!-- On click: app.executeScientificFunction('sqrt') -->

<!-- Memory buttons -->
<button data-memory="add">M+</button>
<!-- On click: app.executeMemoryFunction('add') -->
```

### Keyboard Events

```javascript
// Automatically handled
document.addEventListener('keydown', (e) => {
    if (e.key >= '0' && e.key <= '9') logic.append(e.key);
    if (e.key === '+') logic.setOperation('+');
    if (e.key === 'Enter') logic.calculate();
    // ... etc
});
```

**Supported keys:**
- `0-9` - Input digits
- `+`, `-`, `*`, `/`, `^` - Operators
- `.` - Decimal
- `Enter`, `=` - Calculate
- `Backspace` - Toggle sign
- `c` - Clear
- `h` - Toggle history
- `s` - Toggle scientific mode

---

## Data Structures

### History Object

```javascript
// History is array of strings
[
    "5 + 3 = 8",
    "10 × 2 = 20",
    "√16 = 4",
    "sin(90°) = 1"
]
```

### Theme Object

```javascript
// Themes apply CSS variables
{
    'dark': { /* Default CSS vars */ },
    'light': { /* Light colors */ },
    'ocean': { /* Blue colors */ },
    'sunset': { /* Orange colors */ },
    'forest': { /* Green colors */ }
}
```

### Display State

```javascript
{
    displayValue: "123.45",
    previousValue: 100,
    operation: "+",
    errorState: false,
    waitingForNewValue: false,
    angleMode: "deg",
    memory: 50
}
```

---

## Examples

### Example 1: Basic Calculation

```javascript
const logic = new CalculatorLogic();

logic.append('10');
logic.setOperation('+');
logic.append('5');
const result = logic.calculate();

console.log(result);  // Output: "15"
```

### Example 2: Scientific Calculation

```javascript
const logic = new CalculatorLogic();

logic.displayValue = '45';      // 45 degrees
const sineResult = logic.sine();

console.log(sineResult);        // Output: "0.70710678..."
```

### Example 3: Using Memory

```javascript
const logic = new CalculatorLogic();

// Calculate first part: 10 + 5
logic.append('10');
logic.setOperation('+');
logic.append('5');
logic.calculate();              // Result: "15"

// Store in memory
logic.memoryAdd();              // Memory: 15

// Calculate second part: 3 * 4
logic.clear();
logic.append('3');
logic.setOperation('*');
logic.append('4');
logic.calculate();              // Result: "12"

// Add to memory
logic.memoryAdd();              // Memory: 27

// Use memory value
logiclogic.memoryRecall();       // Display: "27"
logic.setOperation('+');
logic.append('8');
logic.calculate();              // Result: "35"
```

### Example 4: Theme Control

```javascript
const app = new CalculatorApp();

// Apply different themes
app.applyTheme('ocean');        // Ocean theme
setTimeout(() => {
    app.applyTheme('sunset');   // Switch to sunset
}, 3000);
```

### Example 5: Keyboard Integration

```javascript
// Custom keyboard handler
document.addEventListener('keydown', (e) => {
    if (e.ctrlKey && e.key === 'r') {
        // Ctrl+R: Reset and clear
        app.logic.clear();
        app.updateDisplay();
    }
});
```

---

## Troubleshooting

### Issue: Display doesn't update

**Solution:**
```javascript
// Make sure to call updateDisplay() after logic changes
logic.append('5');
app.updateDisplay();  // Essential!
```

---

### Issue: Memory not working

**Solution:**
```javascript
// Check if memory value is accessible
console.log(logic.getMemoryValue());  // Should log number

// Make sure to call updateMemoryDisplay()
logic.memoryAdd();
app.updateMemoryDisplay();  // Updates M: indicator
```

---

### Issue: Scientific functions not available

**Solution:**
```javascript
// Make sure scientific mode is enabled
app.toggleScientificMode();  // Enable first

// Then use functions
logic.sqrt();
```

---

### Issue: Theme not applying

**Solution:**
```javascript
// Use valid theme name
app.applyTheme('ocean');    // ✅ Works

app.applyTheme('blue');     // ❌ Invalid - use 'ocean'

// Check current theme
console.log(document.body.getAttribute('data-theme'));
```

---

## Advanced Usage

### Extending CalculatorLogic

```javascript
// Add custom function
CalculatorLogic.prototype.customFunction = function() {
    const num = parseFloat(this.displayValue);
    this.displayValue = String(num * 2);  // Example: double value
    return this.displayValue;
};

// Use it
logic.customFunction();
```

### Custom Event Handlers

```javascript
// Override default handler
const originalCalculate = logic.calculate.bind(logic);

logic.calculate = function() {
    console.log("Calculating...");
    const result = originalCalculate();
    console.log("Result:", result);
    return result;
};
```

---

## Related Documentation

- 📖 [README.md](README.md) - Overview
- 📚 [DOCS.md](DOCS.md) - User guide
- ⚙️ [Contributing Guide](CONTRIBUTING.md) - Development
- 📥 [Installation Guide](INSTALLATION.md) - Setup

---

## Support

- 🐛 [Report Issues](https://github.com/yourusername/nexus-calculator/issues)
- 💬 [Ask Questions](https://github.com/yourusername/nexus-calculator/discussions)

---

**Last Updated:** April 5, 2026
**Version:** 1.0+
