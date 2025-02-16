Sure! **Singleton** is a design pattern that ensures **only one instance** of an object is created and provides a global point of access to it.  

### **🚀 Key Characteristics of a Singleton:**
1. **Single Instance** → Only **one instance** exists in the entire application.
2. **Global Access** → It can be accessed from anywhere in the app.
3. **Lazy Initialization (Optional)** → The instance is created only when needed.

---

## **1️⃣ Basic Singleton using an Object Literal**
Since JavaScript modules are **cached after the first import**, an **object literal** naturally behaves like a Singleton.
```js
// dataManager.js
export const dataManager = {
  data: [],

  add(item) {
    this.data.push(item);
  },

  getData() {
    return this.data;
  },
};

// main.js
import { dataManager } from './dataManager.js';

dataManager.add("A");
console.log(dataManager.getData()); // ["A"]
```
🔹 **Why is this a singleton?**  
Because `dataManager` is just an **object**, and in ES Modules, the imported object is **shared across all imports**.

---

## **2️⃣ Singleton using a Factory Function**
This method prevents direct modification of properties and ensures **only one instance** exists.

```js
// singletonManager.js
const singletonManager = (function () {
  let instance;

  function createInstance() {
    return {
      data: [],
      add(item) {
        this.data.push(item);
      },
      getData() {
        return this.data;
      }
    };
  }

  return {
    getInstance() {
      if (!instance) {
        instance = createInstance(); // Creates instance only once
      }
      return instance;
    }
  };
})();

// main.js
import singletonManager from './singletonManager.js';

const instance1 = singletonManager.getInstance();
const instance2 = singletonManager.getInstance();

instance1.add("A");
console.log(instance2.getData()); // ["A"] (Same instance)
console.log(instance1 === instance2); // true ✅ (Only one instance)
```
🔹 **Why is this a singleton?**  
- `getInstance()` ensures that only **one object** is ever created.  
- No matter how many times you call `getInstance()`, you always get the **same object**.

---

## **3️⃣ Class-Based Singleton**
In modern JavaScript (ES6+), you can also implement a Singleton using a **class**.

```js
// SingletonClass.js
class Singleton {
  constructor() {
    if (!Singleton.instance) {
      this.data = [];
      Singleton.instance = this; // Store instance in static property
    }
    return Singleton.instance;
  }

  add(item) {
    this.data.push(item);
  }

  getData() {
    return this.data;
  }
}

export default new Singleton(); // Export a single instance
```
```js
// main.js
import singleton from './SingletonClass.js';

singleton.add("B");
console.log(singleton.getData()); // ["B"]
```
🔹 **Why is this a singleton?**  
- `Singleton.instance` stores the **only instance** and prevents new ones from being created.
- The `export default new Singleton();` ensures only **one instance** is shared.

---

## **🔹 When Should You Use a Singleton?**
✅ **Useful for:**
- **Configuration settings** (e.g., app-wide settings or logging systems)
- **Managing shared resources** (e.g., database connections)
- **Caching data** (e.g., storing API results)

❌ **Avoid it when:**
- It **introduces global state** that could be **hard to manage** in large apps.
- You need **multiple independent instances** instead.
