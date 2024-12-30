# OOP-Notes

### Explanation of Static Methods

In object-oriented programming, a **static method** is a method that belongs to the class itself rather than an instance of the class. In TypeScript, static methods are defined using the `static` keyword. These methods can be invoked without creating an instance of the class. 

Static methods are typically used for utility functions or operations that don’t require access to instance-specific data. They provide a way to encapsulate reusable functionality without requiring an object of the class.

---

### Key Characteristics of Static Methods:

1. **Class-Level Access:**
   - Static methods are accessed using the class name, not an instance of the class.
   - Example: `CommonUtils.generateHash(password)` (directly calls the static method).

2. **No Access to `this`:**
   - Static methods don’t have access to `this` because they are not tied to any specific instance of the class.
   - They cannot access non-static properties or methods of the class unless an instance is explicitly created.

3. **Use Cases:**
   - Utility functions like hashing, encryption, formatting, or mathematical operations.
   - Shared logic or operations that don’t depend on instance-specific data.
   - Factory methods to create instances of a class.

4. **Reusability:**
   - Since static methods are tied to the class, they can be reused without needing to create multiple instances of the class.

5. **Cannot be Overridden:**
   - Static methods cannot be overridden by subclass instances, but they can be hidden if the subclass defines a static method with the same name.

---

### Advantages of Static Methods:

1. **Memory Efficiency:**
   - No need to instantiate objects, saving memory when only a class-wide operation is required.

2. **Encapsulation of Utility Functions:**
   - Static methods allow grouping of related helper functions within a class for better organization.

3. **Easier to Test:**
   - Since static methods don’t rely on instance-specific data, they are easier to test in isolation.

---

### Example: `CommonUtils` Class

The provided `CommonUtils` class is a great example of using static methods. Here's why:

1. **Utility Functions:**
   - Methods like `generateHash`, `generateRandomString`, and `validateHash` provide reusable utilities that don’t depend on any instance.

2. **Shared Logic:**
   - Methods like `encrypt` and `decrypt` encapsulate encryption logic for the entire application.

3. **Formatting and Conversions:**
   - Methods like `formatDuration`, `formatDateToCommonFormat`, and `convertedPriceToLocalString` handle commonly needed operations that are independent of any specific object.

4. **Encapsulation of Common Operations:**
   - Operations like `getTravellerType`, `calcDay`, and `getDeviceType` are logically grouped in a single class, improving organization and reusability.

---

### Example Usage of a Static Method

```typescript
const password = "mySecurePassword123";

// Generate a hash for the password using the static method
const hashedPassword = CommonUtils.generateHash(password);

// Validate the password against the hash
const isValid = CommonUtils.validateHash(password, hashedPassword);

console.log(`Password is valid: ${isValid}`);
```

---

### Important Notes on Static Methods:

- **When Not to Use:**
  - If a method needs to access or modify instance-specific data or properties, it cannot be static.
  - Use instance methods for behavior tied to individual objects of a class.

- **Good Practice:**
  - Use static methods for operations that logically belong to the class but don’t need instance-specific context.
  - Keep utility-focused code separate from instance-related logic.

By organizing the `CommonUtils` class this way, you’ve ensured that the static methods provide a centralized, reusable set of functionalities for your application.
