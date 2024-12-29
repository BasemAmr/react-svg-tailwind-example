# react-svg-tailwind-example

# Vite Configuration for SVG as React Components with SVGR/Rollup

### 1. **install `svgr`**
```bash
npm install --save-dev @svgr/rollup
```

### 2. **`vite.config.ts`**
This is the Vite configuration file, which includes the setup for SVGR/Rollup.

```typescript
import react from "@vitejs/plugin-react";
import { defineConfig } from "vite";
import svgr from "@svgr/rollup";

export default defineConfig({
  plugins: [
    react(),
    svgr({
      exportType: "named",
      ref: true,
      svgo: false,
      dimensions: false,
      typescript: true,
    }),
  ]
});
```
### 3. **`custom.d.ts`**
Create this in your src directory

```typescript
declare module "*.svg" {
  import * as React from "react";

  export const ReactComponent: React.FunctionComponent<
    React.SVGProps<SVGSVGElement> & { title?: string }
  >;

  export default ReactComponent;
}
```

### 4. **Use as:**
```typescript
import { ReactComponent as YourImage } from "path-to-your-image.svg";
```



