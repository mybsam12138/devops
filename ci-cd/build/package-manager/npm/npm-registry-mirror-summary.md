# 📦 npm Registry & Mirror — Complete Engineering Summary

---

## 1. What is npm Registry?

### Definition

npm registry is the **official package repository service** used by npm to publish, store, and distribute JavaScript packages.

---

### Core Responsibilities

- Store package metadata:
  - name
  - version
  - dependencies
- Store package artifacts:
  - `.tgz` files (tarballs)
- Provide APIs for:
  - install (`npm install`)
  - publish (`npm publish`)
  - search

---

### Official Registry

- URL: https://registry.npmjs.org

---

### How npm interacts with registry

```
npm install react
        ↓
request registry API
        ↓
receive metadata (JSON)
        ↓
download tarball (.tgz)
        ↓
extract to node_modules
```

---

## 2. What is npm Mirror?

### Definition

An npm mirror is a **replicated registry service** that synchronizes data from the official npm registry and exposes the same API interface.

---

### Example

- https://registry.npmmirror.com

---

### Key Characteristics

- Synchronizes data from official registry
- Provides identical API structure
- May have slight delay (eventual consistency)
- Acts as a cache/CDN layer

---

### Architecture

```
Official Registry
        ↓
   Mirror Sync
        ↓
 Mirror Registry
        ↓
   npm install
```

---

## 3. Differences: Registry vs Mirror

| Aspect            | Official Registry        | Mirror Registry              |
|------------------|------------------------|------------------------------|
| Source           | Original               | Synced from official         |
| Authority        | ✅ Yes                 | ❌ No                        |
| Data freshness   | Real-time              | Slight delay                 |
| Availability     | Global                 | Region-optimized             |
| Control          | Full control           | Read-only (mostly)           |

---

## 4. Why npm Supports Mirrors?

### 1. Performance Optimization

- Reduce latency
- Faster downloads via geographic proximity
- CDN-like behavior

---

### 2. Reliability & Availability

- Avoid single point of failure
- Continue working if official registry is slow/down

---

### 3. Enterprise Use Cases

Companies often use mirrors for:

- Internal caching
- Security control
- Dependency stability
- Offline builds

---

### 4. Network Constraints

- Useful in restricted regions (e.g., China)
- Reduce cross-border network issues

---

## 5. What Format Must a Registry Support?

npm does NOT require "official registry"

👉 It only requires:

> **A server that follows the npm registry protocol (HTTP + JSON + tarball)**

---

### Required Components

#### 1. HTTP API

- RESTful endpoints
- Example:
  GET /react

---

#### 2. Metadata (JSON format)

Example:

{
  "name": "react",
  "versions": {
    "18.2.0": {
      "dist": {
        "tarball": "https://registry/.../react-18.2.0.tgz"
      }
    }
  }
}

---

#### 3. Tarball Hosting

- Package files must be downloadable
- Format: `.tgz`

---

#### 4. Semver Support

- Version resolution must follow semver rules

---

#### 5. Optional Features

- Authentication
- Scoped packages (`@scope/package`)
- Access control

---

## 6. Key Engineering Insight

👉 npm does not care **who provides the registry**

It only cares:

- Does it return correct JSON?
- Can it provide tarballs?
- Does it follow protocol?

---

### Final Summary

- npm registry = **source of truth**
- npm mirror = **replicated + accelerated access layer**
- npm supports mirrors because:
  - performance
  - reliability
  - enterprise control
- registry must support:
  - HTTP API
  - JSON metadata
  - tarball download

---

## 7. Real-World Analogy

- Registry = 🏭 Factory
- Mirror = 🏬 Warehouse / CDN

👉 Same goods, different access speed and location
