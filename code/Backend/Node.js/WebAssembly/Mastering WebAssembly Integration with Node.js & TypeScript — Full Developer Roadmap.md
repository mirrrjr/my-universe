### 📦 Prerequisites:

- Basic JavaScript / Node.js knowledge
    
- Familiarity with terminal and file systems
    
- TypeScript fundamentals (for advanced sections)
    

---

## 📘 **MODULE 1: Introduction to WebAssembly**

### 1.1 What is WebAssembly?

- Why WASM exists
    
- WASM vs JavaScript: performance and purpose
    
- Binary format and `.wat` text format
    

### 1.2 How Node.js and WASM Work Together

- WASM as a module
    
- Loading WASM in Node.js
    
- Using WASM functions like native JavaScript functions
    

### 1.3 Tooling

- Node.js (v16+)
    
- WABT (`wat2wasm`, `wasm2wat`)
    
- Emscripten (for C/C++ → WASM)
    
- wasm-pack (for Rust → WASM)
    
- TypeScript compiler
    

---

## 🧱 **MODULE 2: Hands-on with WAT (WebAssembly Text Format)**

### 2.1 Writing Your First WAT Program

- Syntax: `module`, `func`, `param`, `result`
    
- Memory model and value types (`i32`, `f64`, etc.)
    

### 2.2 Compile and Run

- Compile: `wat2wasm hello.wat -o hello.wasm`
    
- Load and run using Node.js (`WebAssembly.instantiate`)
    

### 2.3 WAT Exercises

- Addition, Subtraction
    
- Multiplication
    
- Using `if`, `block`, `loop`, and `br_if`
    

---

## ⚙️ **MODULE 3: C/C++ to WASM Using Emscripten**

### 3.1 Setting Up Emscripten

- Install via `emsdk`
    
- Compile C/C++ to `.wasm`
    

### 3.2 Running in Node.js

- Exporting functions with `extern "C"`
    
- Passing and returning values
    

---

## 🦀 **MODULE 4: Rust to WASM Using wasm-pack**

### 4.1 Setting Up Rust for WebAssembly

- Target: `wasm32-unknown-unknown`
    
- Install and use `wasm-pack`
    

### 4.2 Importing WASM Module in Node.js

- Using `wasm-bindgen` for bindings
    
- Handling memory safely
    

---

## 🔁 **MODULE 5: Passing Data Between JS/TS and WASM**

### 5.1 Integers and Floats

- How simple values are passed
    

### 5.2 Strings and Arrays

- Working with memory and pointers
    
- `TextEncoder` and `TextDecoder` in JavaScript/TS
    
- Writing helper functions to simplify interop
    

---

## 🚀 **MODULE 6: TypeScript Integration with WASM**

### 6.1 Loading WASM Modules in TS

- Declaring `.wasm` types with `*.d.ts`
    
- Using `fetch` or `fs.readFileSync` with `WebAssembly.instantiate`
    

### 6.2 Type-Safe WASM Interfaces

- Defining types for imports/exports
    
- Using `interface` and `type` for module signatures
    

### 6.3 Creating a WASM Wrapper Class

- Encapsulate WASM loading and calling logic in a TS class
    

### 6.4 Full Project: TypeScript + WASM Math Library

---

## 🔬 **MODULE 7: Advanced Interfacing and Memory Management**

### 7.1 Shared Memory

- Linear memory management in WASM
    
- Using `WebAssembly.Memory` in JS/TS
    

### 7.2 Working with Structs & Buffers

- Serializing/deserializing data
    
- Working with `ArrayBuffer`, `DataView`, `TypedArray`
    

---

## 🔧 **MODULE 8: Testing, Debugging & Performance**

### 8.1 Unit Testing WASM Functions

- Using Jest or Mocha with `.wasm` modules
    

### 8.2 Debugging Techniques

- Source maps
    
- `wasm2wat` for reverse-engineering binaries
    

### 8.3 Performance Benchmarks

- Compare JS vs WASM for heavy computation
    

---

## 🛠️ **MODULE 9: Building a Real-world Node.js + TypeScript + WASM App**

### 9.1 App Idea: WASM-powered API

- Example: `/api/add?a=5&b=6 → returns 11` using WASM
    

### 9.2 Structure:

```
/src
  /wasm
    add.wat → add.wasm
  /ts
    wasm-loader.ts
    api.ts
index.ts
```

### 9.3 API with Express + TypeScript

- Load WASM once and cache
    
- Handle dynamic parameters
    

---

## 🌐 **MODULE 10: Bonus – WebAssembly in the Browser with TypeScript**

### 10.1 Bundling `.wasm` with Webpack or Vite

### 10.2 Frontend UI (React or Vanilla) calling WASM

### 10.3 Fullstack Setup: Same `.wasm` module on backend (Node.js) and frontend (Browser)

---

### 🧠 Final Projects & Capstone Ideas:

- WASM math engine
    
- Text parser/tokenizer with WASM
    
- Crypto hash validator
    
- Game physics engine core in WASM
    
- AI model prediction in WASM
    