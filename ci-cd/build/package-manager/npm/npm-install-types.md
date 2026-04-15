# npm Install Types — Complete Guide

## 🧠 Overview

npm installs packages in different ways depending on their purpose. Understanding these types helps you manage dependencies correctly in real projects.

---

# 📦 1. Dependencies (Runtime)

## ✅ Purpose
Used by your application **at runtime**

## 📥 Install
```bash
npm install express
```

## 📁 Location
```
node_modules/express
```

## 📄 package.json
```json
"dependencies": {
  "express": "^4.18.0"
}
```

## 🚀 Usage
```js
const express = require('express');
```

---

# 🛠️ 2. Dev Dependencies (Development Only)

## ✅ Purpose
Used during development (build, test, lint), NOT in production

## 📥 Install
```bash
npm install vite --save-dev
```

## 📁 Location
```
node_modules/vite
```

## 📄 package.json
```json
"devDependencies": {
  "vite": "^5.0.0"
}
```

## 🚀 Usage

Run via npx:
```bash
npx vite
```

Or via scripts:
```json
"scripts": {
  "dev": "vite"
}
```

```bash
npm run dev
```

---

# 🖥️ 3. CLI Tools

## ✅ Purpose
Used as **commands in terminal**, not directly imported in code

---

## 🔹 Global CLI

### 📥 Install
```bash
npm install -g typescript
```

### 📁 Location
Global node_modules + PATH

### 🚀 Usage
```bash
tsc -v
```

---

## 🔹 Local CLI

### 📥 Install
```bash
npm install vite
```

### 📁 Location
node_modules/.bin

### 🚀 Usage
```bash
npx vite
```

---

# 🔗 4. Peer Dependencies

## ✅ Purpose
Require the user/project to install a compatible dependency manually

## 📄 package.json
```json
"peerDependencies": {
  "react": "^18.0.0"
}
```

## 🚀 Usage
```bash
npm install react
```

---

# ⚙️ 5. Optional Dependencies

## ✅ Purpose
Optional features; installation failure will NOT break the project

## 📥 Install
```bash
npm install some-package --save-optional
```

---

# 📊 Comparison Table

| Type | Install Command | Location | Used By | Example |
|------|---------------|----------|--------|--------|
| dependencies | npm install express | node_modules | runtime | require('express') |
| devDependencies | npm install vite --save-dev | node_modules | dev/build | npx vite |
| global CLI | npm install -g typescript | global + PATH | terminal | tsc |
| local CLI | npm install vite | node_modules/.bin | terminal | npx vite |
| peerDependencies | defined in package.json | not auto-installed | ecosystem | install manually |
| optionalDependencies | --save-optional | node_modules | optional | safe fail |

---

# 🧠 Final Summary

- dependencies → run your app  
- devDependencies → build your app  
- CLI tools → run commands  
- peerDependencies → compatibility  
- optionalDependencies → optional features
