
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

Un comment an set to `./dist`.

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

### Result

The `tsconfig.json` file should look like this:

```json
{
  "compilerOptions": {
    "target": "es2022", 
    "module": "CommonJS",
    "declaration": true,
    "outDir": "./dist",
    "strict": true,
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true,
    "skipLibCheck": true,
  },
  "include": ["src"],
  "exclude": ["node_modules", "**/__tests__/*"],
}
```

The other already uncommented compiler options by default are:

```json
"module": "CommonJS",
```

This setting defines how TypeScript should handle module resolution.
This will use the CommonJS module system, making it compatible with Node.js and other environments that support CommonJS.

```json
"strict": true,
```

This enables strict type-checking options in TypeScript, which ensures the highest level of type safety. Enabling strict helps catch bugs and issues early by enforcing stronger type-checking rules.

```json
"esModuleInterop": true,
```

This makes it easier to import CommonJS modules (e.g., Node.js modules or third-party libraries) in an ES6-style. Without this, importing such modules can require more verbose syntax.

```json
"forceConsistentCasingInFileNames": true,
```

This ensures that the casing of your import paths exactly matches the actual file names. This helps prevent bugs in case-sensitive file systems like Linux.

```json
"skipLibCheck": true,
```

This skips type-checking for `.d.ts` files in third-party libraries, which can speed up compilation and avoid issues that aren't directly related to your own code.




## Update `package.json` Scripts

Modify your `package.json` to include build scripts:

```json
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "clean": "rimraf ./dist",
    "build": "npm run clean && tsc",
    "start": "ts-node src/index.ts",
    "js": "npm run build && node dist/index.js",
    "debug": "node --inspect-brk -r ts-node/register src/index.ts"
  },
  "files": [
    "dist"
  ],
```

Name this commit: node scripts: start, build, etc.

### Script explantion

`"files": ["dist"]` tells npm to only include the dist directory when publishing the package or when someone installs it.

```bash
npm start
```

Runs the `src/index.ts` directly.

```bash
npm run clean
```

Delete the `./dist` directory.

```bash
npm run build
```

Delete the `./dist` directory and compile to JavaScript. The generarted files will be in the `./dist` directory.

```bash
npm run js
```

Delete the `./dist` directory, compiles to JavaScript and runs the `./dist/index.js` file.

```bash
npm run debug
```

Runs the `src/index.ts` file in debug mode listening in a port and wating VSCode to connect and start the debugging proccess.




## Configurate VSCode for debugging

In the root folder create a folder called `.vscode`, inside create a json files named `launch.json` and fill with this code:

```json
{
  // Use IntelliSense to learn about possible attributes.
  // Hover to view descriptions of existing attributes.
  // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Attach",
      "port": 9229,
      "request": "attach",
      "skipFiles": [
        "<node_internals>/**"
      ],
      "type": "node"
    },
    {
      "type": "node",
      "request": "launch",
      "name": "index.ts with ts-node",
      "skipFiles": ["<node_internals>/**"],
      "program": "${workspaceFolder}/src/index.ts",
      "runtimeArgs": ["--inspect-brk", "-r", "ts-node/register"],
      "sourceMaps": true,
      "outFiles": ["${workspaceFolder}/**/*.js"]
    }
  ]
}

```

Name this commit: vscode config. debug by attach and ts-node.
