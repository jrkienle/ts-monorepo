# Code Guidelines

## 👋 Introduction

You may be wondering why I'd go through all of this effort to write code guidelines for a personal
repo. To be completely honest, I found myself asking the same question after I had the impulsive
idea to start writing these. Ultimately the reason I came up with was simple: practice. I want to
treat this repo like it's a real project in a real org wherever possible to ensure I don't get out
of practice managing large, production-ready codebases. With that in mind, here is a living
document that contains my own personal code guidelines. Enjoy!

## 📖 Table of Contents

1. [🎨 Code Style](#code-style)
2. [📦 `package.json`](#-packagejson)

## 🎨 Code Style

Every file in this repo adheres to Prettier's default code style with the following changes:

1. `printWidth` is set to `100`
2. `singleQuote` is set to `true`
3. `trailingComma` is set to `es5`

If you're using Zed, Prettier formatting will be automatically applied to each file on-save.

## 📦 `package.json`

The `package.json` file is required for all apps and packages in the monorepo. It provides
important metadata to NPM for published packages as well as provides Bun with a list of required
dependencies to install.

### Key Sorting

The following keys should appear in the order presented here, and must be the first keys in
every package.json file:

1. `name`
2. `version`
3. `description`
4. `scripts`

**✅ Correct Example:**

```json
{
  "name": "@jrkienle/my-package",
  "version": "0.1.0",
  "description": "Some short yet useful one-sentence description",
  "scripts": {
    "do-something": "echo \"Imagine this script does something\""
  }
}
```

**🚫 Incorrect Example (Missing Required Fields):**

```json
{
  "name": "@jrkienle/my-package",
  "scripts": {
    "do-something": "echo \"Imagine this script does something\""
  }
}
```

**🚫 Incorrect Example (Fields Not First in File):**

```json
{
  "author": "James Kienle",
  "name": "@jrkienle/my-package",
  "version": "0.1.0",
  "description": "Some short yet useful one-sentence description",
  "scripts": {
    "do-something": "echo \"Imagine this script does something\""
  }
}
```

**🚫 Incorrect Example (Incorrect Order):**

```json
{
  "name": "@jrkienle/my-package",
  "description": "Some short yet useful one-sentence description",
  "version": "0.1.0",
  "scripts": {
    "do-something": "echo \"Imagine this script does something\""
  }
}
```

All remaining keys should be sorted in alphabetical order. If any values contain children (for
instance, an array or object), the children must also be sorted in alphabetical order".

**✅ Correct Example:**

```json
{
  "name": "@jrkienle/my-package",
  "version": "0.1.0",
  "description": "Some short yet useful one-sentence description",
  "scripts": {},
  "author": "James Kienle",
  "devDependencies": {
    "@types/bun": "latest",
    "typescript": "^5.5.2"
  },
  "keywords": ["jrkienle"]
}
```

**🚫 Incorrect Example (Incorrect Key Order):**

```json
{
  "name": "@jrkienle/my-package",
  "description": "Some short yet useful one-sentence description",
  "version": "0.1.0",
  "scripts": {},
  "devDependencies": {
    "@types/bun": "latest",
    "typescript": "^5.5.2"
  },
  "author": "James Kienle",
  "keywords": ["example", "jrkienle"]
}
```

**🚫 Incorrect Example (Incorrect Child Order):**

```json
{
  "name": "@jrkienle/my-package",
  "description": "Some short yet useful one-sentence description",
  "version": "0.1.0",
  "scripts": {},
  "author": "James Kienle",
  "devDependencies": {
    "typescript": "^5.5.2",
    "@types/bun": "latest"
  },
  "keywords": ["jrkienle", "example"]
}
```

### Required Fields for All Packages

This repo only uses ESM. Because of this, the `type` field is required in every `package.json`
and must be set to `module`.

**✅ Correct Example:**

```json
{
  "name": "@jrkienle/my-package",
  "description": "Some short yet useful one-sentence description",
  "version": "0.1.0",
  "scripts": {},
  "type": "module"
}
```

**🚫 Incorrect Example (Incorrect Value):**

```json
{
  "name": "@jrkienle/my-package",
  "description": "Some short yet useful one-sentence description",
  "version": "0.1.0",
  "scripts": {},
  "type": "commonjs"
}
```

**🚫 Incorrect Example (Key Omitted):**

```json
{
  "name": "@jrkienle/my-package",
  "description": "Some short yet useful one-sentence description",
  "version": "0.1.0",
  "scripts": {}
}
```

### Required Fields for Public Packages

For packages that are intended on being published, the following keys are required:

- `author`
- `bugs`
- `homepage`
- `keywords`
- `license`
- `repository`

**✅ Correct Example:**

```json
{
  "name": "@jrkienle/my-package",
  "description": "Some short yet useful one-sentence description",
  "version": "0.1.0",
  "scripts": {},
  "author": "James Kienle",
  "bugs": {
    "url": "https://github.com/jrkienle/ts-monorepo/issues"
  },
  "homepage": "https://github.com/jrkienle/ts-monorepo/tree/main/packages/my-package#readme",
  "keywords": ["jrkienle"],
  "license": "MIT",
  "repository": {
    "type": "git",
    "url": "git+https://github.com/jrkienle/ts-monorepo.git"
  },
  "type": "module"
}
```

**🚫 Incorrect Example (Missing Fields):**

```json
{
  "name": "@jrkienle/my-package",
  "description": "Some short yet useful one-sentence description",
  "version": "0.1.0",
  "scripts": {},
  "author": "James Kienle",
  "homepage": "https://github.com/jrkienle/ts-monorepo/tree/main/packages/my-package#readme",
  "keywords": [],
  "license": "MIT",
  "type": "module"
}
```

### Required Fields for Private Packages

For packages that are **not** intended on being published, the following keys are required:

- `private` (must be set to `true`)

**✅ Correct Example:**

```json
{
  "name": "@jrkienle/my-package",
  "description": "Some short yet useful one-sentence description",
  "version": "0.1.0",
  "scripts": {},
  "private": true,
  "type": "module"
}
```

**🚫 Incorrect Example (Incorrect Value):**

```json
{
  "name": "@jrkienle/my-package",
  "description": "Some short yet useful one-sentence description",
  "version": "0.1.0",
  "scripts": {},
  "private": false,
  "type": "module"
}
```

**🚫 Incorrect Example (Key Omitted):**

```json
{
  "name": "@jrkienle/my-package",
  "description": "Some short yet useful one-sentence description",
  "version": "0.1.0",
  "scripts": {},
  "type": "module"
}
```
