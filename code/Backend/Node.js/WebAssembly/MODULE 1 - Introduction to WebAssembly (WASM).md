

---

### 🧩 **Lesson 1.1 — What is WebAssembly (WASM)?**

#### 🔹 **Definition:**

WebAssembly (WASM) — bu **yuqori darajadagi tillardan (C, C++, Rust)** yozilgan dasturlarni **brauzerda yoki serverda** (Node.js) juda **tez** ishlatish uchun mo‘ljallangan _binar formatdagi_ til.

#### 🔹 **Key Features:**

- 🧠 **Low-level & portable:** Machine-like instructions, runs almost everywhere
    
- 🚀 **Fast execution:** Close to native C/C++ performance
    
- 🔒 **Sandboxed:** Secure runtime — no direct file system or memory access
    
- 📦 **Language-neutral:** Write in C/C++/Rust, compile to `.wasm`
    
- 🌐 **Browser & server compatibility:** Works in Chrome, Firefox, Safari, and Node.js
    

#### 🔹 **Use Cases:**

|Scenario|Why WASM?|
|---|---|
|Game engines|High performance|
|Video/image editing in browser|Near-native speed|
|Machine learning inference|Efficient CPU usage|
|Crypto operations|Fast and secure|
|Reusing legacy C/C++ code|No need to rewrite in JS|

---

### ⚔️ **WASM vs JavaScript: Comparison**

|Feature|WebAssembly|JavaScript|
|---|---|---|
|Type system|Static (typed)|Dynamic|
|Execution speed|Very fast|Slower for heavy tasks|
|Memory access|Manual, low-level|Abstracted|
|File size|Compact binary|Text|
|Debugging|Harder (but improving)|Easy|
|Interoperability|Can be called from JS|Works natively in browser|

---

### 🔬 **Lesson 1.2 — How WASM & Node.js work together**

#### 🔹 Workflow:

```bash
source.wat (or .c/.rs) → wat2wasm / emscripten / wasm-pack → module.wasm → load in Node.js
```

#### 🔹 Node.js APIs used:

- `fs.readFileSync()` — read WASM file
    
- `WebAssembly.instantiate()` — compile & execute
    

> ✅ Once instantiated, you can call WASM-exported functions just like regular JS functions!

---

### 🛠️ **Lesson 1.3 — Installing Required Tools**

#### 🔸 Install Node.js:

```bash
sudo apt update
sudo apt install nodejs npm
node -v
```

#### 🔸 Install `wabt` (WebAssembly Binary Toolkit):

```bash
sudo apt install wabt
```

> This gives you `wat2wasm`, which lets you compile `.wat` text files to `.wasm`.

---

### ✅ What You’ve Learned So Far:

- What WebAssembly is, and why it matters
    
- How it compares to JavaScript
    
- The toolchain for running WASM in Node.js
    

---

## 🔜 **Next Lesson (1.4): Write your first WebAssembly module in WAT format**

In the next lesson, we’ll:

- Write a WAT file (`add.wat`)
    
- Compile it to `.wasm`
    
- Run it in Node.js and see how it performs
    

Do you want me to **jump into the first code tutorial right now**, or do you prefer a short quiz or visual summary first?

You choose 😊