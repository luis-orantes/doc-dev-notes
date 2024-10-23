
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




## Configure TypeScript

### Initialize

Initialize a `tsconfig.json` file to configure the TypeScript compiler:

```bash
npx tsc --init
```

This will create a tsconfig.json file with default configurations. 

Name this commit: node and ts initialized.

### Edit

Edit the `target` to a modern JavaScript version.

```json
 "target": "es2022",
```

### Uncomment

Uncomment the next compiler configurations:

```json
"declaration": true,
```

Generate a `.d.ts` file for every `.ts` file that exports something.

```json
"outDir": "./dist",
```

Outputs compiled files to the `./dist` directory.

### Append

Add a comma after in the penultimate closing curling bracket `}` and the the following configurations:

```json
"include": ["src"],
```

This specifies which files TypeScript should include in the compilation process.

```json
"exclude": ["node_modules", "**/__tests__/*"],
```

This option tells TypeScript which files or directories to ignore when compiling. This excludes:

* **`node_modules`**: This is where npm packages are installed. It’s excluded because you don’t want to compile third-party code.

* **`__tests__`**: This excludes files that might be located inside a `__tests__` folder, which are typically used for unit tests. Since these files are not part of your actual codebase, they’re excluded from the compilation.

Name this commit: ts first configuration.
