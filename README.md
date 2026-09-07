# Codescape Core UI

Reusable UI components for Codescape products.

## Tailwind CSS

The components use Tailwind CSS utility classes. Install Tailwind CSS in the
application that consumes this package and include the package's built files in
Tailwind's source scan.

```bash
npm install @codescape/core-ui tailwindcss
```

In the application's main stylesheet:

```css
@import "tailwindcss";
@source "../node_modules/@codescape/core-ui/dist";
```

Adjust the `@source` path when the stylesheet is in a different directory.
