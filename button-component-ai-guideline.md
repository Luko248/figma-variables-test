# AI Guideline: Button Component from Vertice-UI Package

> **Part of [Vertice AI Global Guideline](./vertice-ai-global-guideline.md)**  
> This component guideline follows Vertice's design system standards and development principles.

## Overview

The Button component from the `vertice-ui` package is a highly customizable, accessible button component built on top of Material-UI. It supports multiple variants, sizes, colors, and states including loading and disabled states, designed specifically for Vertice's spend optimization platform interfaces.

**Important Note**: This component is marked as deprecated. Use `Button` from `@vertice-ui/button` instead.

### Alignment with Vertice's Mission

This Button component supports Vertice's core business functions:

- **SaaS Purchasing**: Action buttons for procurement workflows
- **Cloud Cost Optimization**: Controls for cost analysis and optimization actions
- **Intelligent Workflows**: Automation trigger buttons and process controls
- **Spend Analytics**: Interactive elements for data exploration and reporting

## Import Statement

```typescript
import { Button } from "@vertice-ui/button";
```

## Basic Usage

```tsx
// Simple button
<Button>Click me</Button>

// Button with props
<Button
  variant="solid"
  color="primary"
  size="M"
  onClick={handleClick}
>
  Submit
</Button>
```

## Properties Reference

### Core Properties

#### `variant` (DesignSystemVariant)

Controls the visual style of the button.

- **Type**: `'solid' | 'ghost' | 'outline' | 'plain'`
- **Default**: `'outline'`
- **Usage**:
  ```tsx
  <Button variant="solid">Solid Button</Button>
  <Button variant="ghost">Ghost Button</Button>
  <Button variant="outline">Outline Button</Button>
  <Button variant="plain">Plain Button</Button>
  ```

#### `color` (DesignSystemColor)

Sets the color theme of the button.

- **Type**: `'neutral' | 'primary' | 'secondary' | 'tertiary' | 'transparent' | 'success' | 'warning' | 'error' | 'info'`
- **Default**: `'neutral'`
- **Usage**:
  ```tsx
  <Button color="primary">Primary</Button>
  <Button color="success">Success</Button>
  <Button color="error">Error</Button>
  <Button color="warning">Warning</Button>
  ```

#### `size` (DesignSystemSize)

Controls the size of the button.

- **Type**: `'XL' | 'L' | 'M' | 'S' | 'XS' | 'XXS'`
- **Default**: `'M'`
- **Usage**:
  ```tsx
  <Button size="XL">Extra Large</Button>
  <Button size="L">Large</Button>
  <Button size="M">Medium</Button>
  <Button size="S">Small</Button>
  <Button size="XS">Extra Small</Button>
  <Button size="XXS">Extra Extra Small</Button>
  ```

### State Properties

#### `disabled`

Disables the button interaction.

- **Type**: `boolean`
- **Default**: `false`
- **Usage**:
  ```tsx
  <Button disabled>Disabled Button</Button>
  ```

#### `isLoading`

Shows a loading spinner and hides the button content.

- **Type**: `boolean`
- **Default**: `false`
- **Usage**:
  ```tsx
  <Button isLoading>Loading...</Button>
  ```

#### `isActive`

Controls the active state appearance.

- **Type**: `boolean`
- **Default**: `true`
- **Usage**:
  ```tsx
  <Button isActive={false}>Inactive Button</Button>
  ```

### Layout Properties

#### `direction`

Controls the layout direction of button content (useful with icons).

- **Type**: `'horizontal' | 'vertical'`
- **Default**: `'horizontal'`
- **Usage**:
  ```tsx
  <Button direction="vertical">
    <Icon />
    Vertical Layout
  </Button>
  ```

#### `isCircle`

Makes the button circular (useful for icon-only buttons).

- **Type**: `boolean`
- **Default**: `false`
- **Usage**:
  ```tsx
  <Button isCircle>
    <Icon />
  </Button>
  ```

#### `isCaption`

Applies caption styling (smaller text).

- **Type**: `boolean`
- **Default**: `false`
- **Usage**:
  ```tsx
  <Button isCaption>Caption Button</Button>
  ```

### Technical Properties

#### `component`

Allows rendering as a different HTML element or React component.

- **Type**: `React.ElementType`
- **Default**: `'button'`
- **Usage**:
  ```tsx
  <Button component="a" href="/link">Link Button</Button>
  <Button component={Link} to="/route">Router Link</Button>
  ```

#### `testId`

Adds test identifier for testing purposes.

- **Type**: `string`
- **Usage**:
  ```tsx
  <Button testId="submit-button">Submit</Button>
  ```

#### `dataAttributes`

Adds custom data attributes.

- **Type**: `{ [key: \`data-${string}\`]: string }`
- **Usage**:
  ```tsx
  <Button dataAttributes={{ "data-analytics": "submit-click" }}>Submit</Button>
  ```

## Usage Examples

### Basic Buttons

```tsx
// Different variants
<Button variant="solid" color="primary">Solid Primary</Button>
<Button variant="ghost" color="secondary">Ghost Secondary</Button>
<Button variant="outline" color="success">Outline Success</Button>
<Button variant="plain" color="error">Plain Error</Button>
```

### Buttons with Icons

```tsx
import { SaveIcon, DeleteIcon } from '@mui/icons-material';

// Horizontal layout (default)
<Button variant="solid" color="primary">
  <SaveIcon />
  Save Document
</Button>

// Vertical layout
<Button variant="ghost" direction="vertical">
  <DeleteIcon />
  Delete
</Button>

// Icon-only circular button
<Button isCircle variant="solid" color="primary">
  <SaveIcon />
</Button>
```

### Loading States

```tsx
const [isLoading, setIsLoading] = useState(false);

const handleSubmit = async () => {
  setIsLoading(true);
  try {
    await submitForm();
  } finally {
    setIsLoading(false);
  }
};

<Button
  variant="solid"
  color="primary"
  isLoading={isLoading}
  onClick={handleSubmit}
>
  {isLoading ? "Submitting..." : "Submit"}
</Button>;
```

### Different Sizes

```tsx
<Stack direction="row" spacing={2}>
  <Button size="XXS">Tiny</Button>
  <Button size="XS">Extra Small</Button>
  <Button size="S">Small</Button>
  <Button size="M">Medium</Button>
  <Button size="L">Large</Button>
  <Button size="XL">Extra Large</Button>
</Stack>
```

### Form Integration

```tsx
// Submit button
<Button
  type="submit"
  variant="solid"
  color="primary"
  disabled={!isFormValid}
>
  Submit Form
</Button>

// Reset button
<Button
  type="reset"
  variant="outline"
  color="neutral"
>
  Reset
</Button>
```

### Navigation Buttons

```tsx
// As link
<Button
  component="a"
  href="/dashboard"
  variant="ghost"
  color="primary"
>
  Go to Dashboard
</Button>

// With React Router
<Button
  component={Link}
  to="/profile"
  variant="plain"
  color="secondary"
>
  View Profile
</Button>
```

## Accessibility Features

The Button component includes built-in accessibility features:

- **Keyboard Navigation**: Supports Tab and Enter/Space key interactions
- **Focus Management**: Proper focus indicators and outline styles
- **Screen Reader Support**: Semantic button element with proper ARIA attributes
- **Loading State**: Content is hidden but accessible during loading

### Accessibility Best Practices

```tsx
// Use descriptive text
<Button>Save Document</Button> // Good
<Button>Save</Button> // Less descriptive

// Provide context for icon-only buttons
<Button isCircle aria-label="Delete item">
  <DeleteIcon />
</Button>

// Use proper loading states
<Button isLoading aria-label="Submitting form">
  Submit
</Button>
```

## ButtonGroup Integration

The Button component works seamlessly with ButtonGroup:

```tsx
import { ButtonGroup } from "vertice-fe-design-system";

<ButtonGroup variant="outline" color="primary" size="M">
  <Button>First</Button>
  <Button>Second</Button>
  <Button>Third</Button>
</ButtonGroup>;
```

## Styling Customization

The component supports theme-based styling through the design system:

```tsx
// Custom styling through theme
const customTheme = {
  palette: {
    primary: {
      color1: "#custom-color",
      // ... other color definitions
    },
  },
};
```

## Common Patterns

### Action Buttons

```tsx
// Primary action
<Button variant="solid" color="primary" size="M">
  Save Changes
</Button>

// Secondary action
<Button variant="outline" color="neutral" size="M">
  Cancel
</Button>
```

### Status Buttons

```tsx
// Success action
<Button variant="solid" color="success">
  Approve
</Button>

// Destructive action
<Button variant="solid" color="error">
  Delete
</Button>

// Warning action
<Button variant="ghost" color="warning">
  Archive
</Button>
```

### Responsive Buttons

```tsx
// Different sizes for different breakpoints
const buttonSize = useMediaQuery("(max-width: 600px)") ? "S" : "M";

<Button size={buttonSize} variant="solid" color="primary">
  Responsive Button
</Button>;
```

## Migration Notes

When migrating from the deprecated component:

1. Update import to use `@vertice-ui/button`
2. All existing props remain the same
3. Styling and behavior are preserved
4. Test thoroughly in your specific use cases

## Performance Considerations

- The component uses React.forwardRef for proper ref forwarding
- Styled components are memoized for performance
- Loading states are optimized to prevent layout shifts
- Icon sizing is handled efficiently through CSS

## Testing

```tsx
// Testing with React Testing Library
import { render, screen, fireEvent } from "@testing-library/react";

test("button handles click events", () => {
  const handleClick = jest.fn();
  render(<Button onClick={handleClick}>Click me</Button>);

  fireEvent.click(screen.getByRole("button"));
  expect(handleClick).toHaveBeenCalledTimes(1);
});

test("button shows loading state", () => {
  render(<Button isLoading>Loading</Button>);
  expect(screen.getByRole("button")).toBeInTheDocument();
  // Loading spinner should be visible
});
```

This comprehensive guide covers all aspects of the Button component from the vertice-ui package, including properties, usage patterns, accessibility features, and best practices for implementation.

## Related Guidelines

### Global Guidelines

- **[Vertice AI Global Guideline](./vertice-ai-global-guideline.md)** - Core principles, standards, and approach for all Vertice UI development

### Component Guidelines

- **Form Components** (Coming Soon) - Input, Select, Checkbox, Radio components for data collection
- **Navigation Components** (Coming Soon) - Menu, Breadcrumbs, Tabs for application navigation
- **Data Display** (Coming Soon) - Table, List, Card components for information presentation
- **Feedback Components** (Coming Soon) - Alert, Toast, Modal for user notifications
- **Layout Components** (Coming Soon) - Grid, Stack, Container for page structure

### Integration Examples

The Button component works seamlessly with other Vertice-UI components:

```tsx
// With Form Components
<form>
  <Input label="Cost Threshold" />
  <Button type="submit" variant="solid" color="primary">
    Set Alert
  </Button>
</form>

// With Navigation
<ButtonGroup>
  <Button variant="ghost">Dashboard</Button>
  <Button variant="ghost">Analytics</Button>
  <Button variant="solid" color="primary">Optimize</Button>
</ButtonGroup>

// With Feedback Components
<Modal>
  <Text>Confirm cost optimization changes?</Text>
  <Stack direction="row" spacing={2}>
    <Button variant="outline" color="neutral">Cancel</Button>
    <Button variant="solid" color="primary">Confirm</Button>
  </Stack>
</Modal>
```

---

**Next Steps**: Explore other component guidelines or refer to the [Vertice AI Global Guideline](./vertice-ai-global-guideline.md) for comprehensive development standards and principles.
