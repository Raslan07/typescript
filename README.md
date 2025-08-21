# TypeScript Project Setup Guide

A comprehensive guide to setting up a TypeScript project from scratch with proper project structure and configuration.

## Prerequisites

Before starting, ensure you have the following installed:

- **Node.js**: Download and install from [https://nodejs.org/en](https://nodejs.org/en)
- Verify installation by running:
  ```bash
  node -v
  ```

## Installation

### 1. Install TypeScript Globally

```bash
npm install -g typescript
```

### 2. Verify TypeScript Installation

```bash
tsc -v
```

## Project Setup

### Quick Start Commands

```bash
# Create project directory
mkdir my-typescript-project
cd my-typescript-project

# Install TypeScript globally (if not already done)
npm install -g typescript

# Create project structure
mkdir src
mkdir dist

# Create main TypeScript file
touch src/index.ts

# Initialize TypeScript configuration
tsc --init

# Initialize npm package
npm init -y
```

### Project Structure

After setup, your project should look like this:

```
my-typescript-project/
├── src/
│   ├── index.ts
│   └── utils/
│       └── helper.ts
├── dist/              # Generated files
├── package.json
├── tsconfig.json
└── index.html         # Optional: for web projects
```

## Configuration

### TypeScript Configuration (tsconfig.json)

Replace the generated `tsconfig.json` with the following optimized configuration:

```json
{
  "compilerOptions": {
    // File Layout
    "rootDir": "./src",
    "outDir": "./dist",

    // Environment Settings
    "module": "es6",
    "target": "es6",
    "types": [],
    
    // For Node.js projects, uncomment these:
    // "lib": ["esnext"],
    // "types": ["node"],
    // and run: npm install -D @types/node

    // Output Options
    "sourceMap": true,
    "declaration": true,
    "declarationMap": true,

    // Stricter Type Checking
    "noUncheckedIndexedAccess": true,
    "exactOptionalPropertyTypes": true,
    "forceConsistentCasingInFileNames": true,
    
    // Style Options (uncomment as needed)
    // "noImplicitReturns": true,
    // "noImplicitOverride": true,
    // "noUnusedLocals": true,
    // "noUnusedParameters": true,
    // "noFallthroughCasesInSwitch": true,
    // "noPropertyAccessFromIndexSignature": true,

    // Recommended Options
    "strict": true,
    "jsx": "react-jsx",
    "verbatimModuleSyntax": true,
    "isolatedModules": true,
    "noUncheckedSideEffectImports": true,
    "moduleDetection": "force",
    "skipLibCheck": true
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules", "dist"]
}
```

### Package.json Scripts

Add the following scripts to your `package.json`:

```json
{
  "scripts": {
    "build": "tsc",
    "build:watch": "tsc --watch",
    "clean": "rm -rf dist",
    "start": "node dist/index.js",
    "dev": "ts-node src/index.ts"
  }
}
```

### Optional: Install Development Dependencies

For enhanced development experience:

```bash
npm install -D ts-node @types/node nodemon
```

## Usage

### Building the Project

```bash
# Build once
npm run build

# Build and watch for changes
npm run build:watch

# Clean compiled files
npm run clean
```

### Running the Project

```bash
# Run compiled JavaScript
npm start

# Run TypeScript directly (requires ts-node)
npm run dev
```

### Basic TypeScript Example

**src/index.ts**
```typescript
import { greet } from './utils/helper';

const message: string = greet('World');
console.log(message);
```

**src/utils/helper.ts**
```typescript
export function greet(name: string): string {
  return `Hello, ${name}!`;
}
```

## Web Integration

For web projects, create an `index.html` file in your project root:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TypeScript Project</title>
</head>
<body>
    <h1>My TypeScript Project</h1>
    <script type="module" src="dist/index.js"></script>
</body>
</html>
```

## Additional Resources

- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [TypeScript Playground](https://www.typescriptlang.org/play)
- [TSConfig Reference](https://aka.ms/tsconfig)

## Development Workflow

1. Write TypeScript code in the `src/` directory
2. Run `npm run build:watch` to automatically compile on changes
3. Test your compiled code with `npm start`
4. For web projects, serve your HTML file and check the browser console

## Troubleshooting

- **Module not found errors**: Ensure your import paths are correct and files exist
- **Compilation errors**: Check your `tsconfig.json` configuration
- **Runtime errors**: Verify your compiled JavaScript in the `dist/` folder

---

**Happy coding with TypeScript! 🚀**