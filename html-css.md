# CSS and HTML Fundamentals

## 1. CSS Box Model

The Box Model defines how elements are sized and spaced:

- **Content**: Text or images inside the element.
- **Padding**: Space between content and border.
- **Border**: Surrounds padding.
- **Margin**: Space outside the border.

**Example**:

```css
div {
  width: 200px;
  padding: 10px;
  border: 5px solid black;
  margin: 20px;
}
```

Total width: 200px (content) + 10px (left padding) + 10px (right padding) + 5px (left border) + 5px (right border) = 230px.

## 2. Inline vs. Block Elements

- **Block Elements**: Take full width, start on a new line (e.g., `<div>`, `<p>`).
- **Inline Elements**: Only take needed width, stay in line (e.g., `<span>`, `<a>`).

**Example**:

```html
<div>Block: Takes full width</div>
<span>Inline: Only as wide as content</span>
```

## 3. Positioning: Relative vs. Absolute

- **Relative**: Moves relative to its normal position.
- **Absolute**: Moves relative to the nearest positioned ancestor or the document.

**Example**:

```css
.relative {
  position: relative;
  top: 10px; /* Moves down 10px from original spot */
}
.absolute {
  position: absolute;
  top: 20px; /* Moves 20px from top of parent */
}
```

## 4. Common CSS Structural Classes

Structural classes control layout:

- `.container`: Centers content with max-width.
- `.row`: Aligns items horizontally.
- `.column`: Aligns items vertically.

**Example**:

```css
.container {
  max-width: 1200px;
  margin: 0 auto;
}
.row {
  display: flex;
}
```

## 5. Common CSS Styling Classes

Styling classes enhance appearance:

- `.text-center`: Centers text.
- `.bg-primary`: Sets a primary background color.
- `.hidden`: Hides elements.

**Example**:

```css
.text-center {
  text-align: center;
}
.bg-primary {
  background-color: #007bff;
}
```

## 6. CSS Specificity

Specificity determines which CSS rule applies when multiple rules target the same element. Rules are scored based on:

- Inline styles (1000 points)
- IDs (100 points)
- Classes, attributes, pseudo-classes (10 points)
- Elements, pseudo-elements (1 point)

**Example**:

```css
#id { color: red; } /* Higher specificity */
.class { color: blue; } /* Lower specificity */
```

## 7. CSS Responsive Queries

Media queries adjust styles based on screen size:

```css
@media (max-width: 600px) {
  body {
    font-size: 16px;
  }
}
```

This reduces font size on screens smaller than 600px.

## 8. Flexbox and Grid

- **Flexbox**: For one-dimensional layouts (row or column).
- **Grid**: For two-dimensional layouts (rows and columns).

**Flexbox Example**:

```css
.container {
  display: flex;
  justify-content: space-between;
}
```

**Grid Example**:

```css
.grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
}
```

## 9. Common Header Meta Tags

Meta tags in `<head>` provide metadata:

- `<meta charset="UTF-8">`: Sets character encoding.
- `<meta name="viewport" content="width=device-width, initial-scale=1.0">`: Ensures responsive design.
- `<meta name="description" content="Site description">`: Describes the page for SEO.

**Example**:

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Website</title>
</head>
```

## 10. Emerging Topic: Container Queries

Container queries (new in 2025) adjust styles based on a parent container’s size, not the viewport:

```css
@container (min-width: 300px) {
  .card {
    font-size: 18px;
  }
}
```

This makes components more reusable across layouts.

## References
- [Mozilla Developer Network.](https://developer.mozilla.org/en-US/docs/Web/CSS)
- [W3C. HTML Living Standard.](https://html.spec.whatwg.org/)