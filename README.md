# Setup NodeJS wtih typescript

## Initialize npm Project

### npm init -y

y flag to skip the prompts for additional information

## Installing dependencies

### npm i -D typescript

### npm i -D tslint

The -D flag is the shortcut for: --save-dev.

### npm i express

### npm i -D @types/express

The second command installs the Express types for TypeScript support.

## Configure typescript

### tsc --init

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "esModuleInterop": true,
    "target": "es6",
    "moduleResolution": "node",
    "sourceMap": true,
    "outDir": "dist"
  },
  "lib": ["es2015"]
}
```

- module: Specifies the module code generation method. Node uses commonjs.
- target: Specifies the output language level.
- moduleResolution: This helps the compiler figure out what an import refers to. The value node mimics the Node module resolution mechanism.
- outDir: This is the location to output .js files after transpilation. In this tutorial you will save it as dist.

### ./node_modules/.bin/tslint --init

TypeScript linting for the project.

```JSON
{
  "defaultSeverity": "error",
  "extends": ["tslint:recommended"],
  "jsRules": {},
  "rules": {
    "no-console": false
  },
  "rulesDirectory": []
}
```

By default, the TypeScript linter prevents the use of debugging using console statements, hence the need to explicitly tell the linter to revoke the default no-console rule.

## Updating the package.json File

```JSON
{
  "name": "node-with-ts",
  "version": "1.0.0",
  "description": "",
  "main": "dist/app.js",
  "scripts": {
    "start": "tsc && node dist/app.js",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "@types/express": "^4.16.1",
    "tslint": "^5.12.1",
    "typescript": "^3.3.3"
  },
  "dependencies": {
    "express": "^4.16.4"
  }
}
```

## Creating and Running a Basic Express Server

### mkdir src

### create a src/app.ts file

```JS
import express from 'express';

const app = express();
const port = 3000;
app.get('/', (req, res) => {
  res.send('The sedulous hyena ate the antelope!');
});
app.listen(port, err => {
  if (err) {
    return console.error(err);
  }
  return console.log(`server is listening on ${port}`);
});
```
