### 4. **Instance Methods vs. Static Methods**
| Feature               | Instance Method                     | Static Method                        |
|-----------------------|-------------------------------------|--------------------------------------|
| **Invocation**        | On an instance (`instance.method()`) | On the class (`Class.method()`)      |
| **`this` Context**    | Refers to the instance              | Refers to the class itself           |
| **Access**            | Can access instance and class properties | Can only access class properties    |
| **Example Use**       | Object-specific behavior (e.g., `calculate()`) | Shared utilities (e.g., `isType()`) |
