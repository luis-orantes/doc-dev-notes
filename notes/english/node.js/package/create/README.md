
# Create a Node.js package with TypeScript




## Initialize the Project

Create a new directory for your package, move the empty directory, and initialize it with npm:

```bash
npm init -y
```




## Install Development Dependencies

```bash
npm install --save-dev typescript ts-node @types/node rimraf
```

- **typescript**: The TypeScript compiler
- **ts-node**: Execute TypeScript files directly
- **@types/node**: Type definitions for Node.js
- **rimraf**: Cross-platform tool to remove directories (used in build scripts)
