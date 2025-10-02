That's an excellent piece of advice from the book, and it touches on one of the most important best practices in the Node.js ecosystem.

The author is recommending that you install most npm packages locally, within your specific project, rather than globally on your computer.

---

## Local vs. Global Installation

### Local Installation (The Recommended Way)

When you run `npm install <package-name>`, the package is installed into the **`node_modules`** folder *inside your project directory*.

* **Definition:** The package is only available to the specific project you are currently working on.
* **Modularity and Isolation:** Each project gets its own isolated, private copy of the package. This is what the author means by **"modularity."** Your project is self-contained and only relies on the files within its folder.

### Global Installation (The Practice to Avoid)

When you run `npm install -g <package-name>`, the package is installed into a single, shared location on your operating system (your "system registry," as you mentioned before).

* **Definition:** The package is available to *any* project on your machine via the command line.
* **Use Case:** This is primarily reserved for tools that you intend to use as **Command-Line Interface (CLI) programs** across different projects, like `nodemon`, `eslint`, or project initializers like `create-react-app`.

---

## Why Global Installation Causes Problems

The author warns against global installs because they cause two major issues:

### 1. Version Conflicts

This is the most common and serious problem. Imagine you have two projects:

* **Project A** was written last year and depends on an older version of a library, say **`lodash@3.0.0`**.
* **Project B** is a new project that requires the latest version of that same library, **`lodash@4.17.0`**.

If you had installed `lodash` globally, you could only have *one* version installed on your system at a time. Project A would break when you update for Project B, or vice-versa. **Local installation** solves this completely because Project A will have its own `lodash@3.0.0` in its `node_modules` folder, and Project B will have its own `lodash@4.17.0` in its folder. They are completely isolated and cannot interfere with each other.

### 2. Reduced Modularity

If your project relies on a globally installed package, it's not truly independent. Someone else who downloads your code must manually remember to install that package globally on their machine before the project will run.

By keeping all dependencies **local** (and listed in your `package.json`), anyone can get your project running by simply typing `npm install`. This makes your project modular, portable, and reliable.

**The Golden Rule:** Only install packages globally if you need to run them directly from the command line across multiple projects (like `nodemon`). For all other code that your application imports (like `lodash` or `express`), **install it locally**.

[G]
