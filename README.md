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

Here’s an explanation of **utility functions**, **shared logic**, and **factory methods**, with practical TypeScript examples for each:

---

### **1. Utility Functions**
Utility functions are reusable methods that perform specific tasks like hashing, encryption, formatting, or mathematical operations. They don’t depend on instance-specific data.

#### Example: Hashing and Formatting Utilities
```typescript
import * as bcrypt from 'bcrypt';

class UtilityFunctions {
    // Hashing a password
    static hashPassword(password: string): string {
        return bcrypt.hashSync(password, 10);
    }

    // Validating a hashed password
    static validatePassword(password: string, hash: string): boolean {
        return bcrypt.compareSync(password, hash);
    }

    // Formatting a number to include commas
    static formatNumber(value: number): string {
        return value.toLocaleString('en-US');
    }
}

// Usage
const password = "secure123";
const hashedPassword = UtilityFunctions.hashPassword(password);
console.log(`Hashed Password: ${hashedPassword}`);

const isValid = UtilityFunctions.validatePassword("secure123", hashedPassword);
console.log(`Password is valid: ${isValid}`);

console.log(`Formatted Number: ${UtilityFunctions.formatNumber(123456789)}`);
```

---

### **2. Shared Logic**
Shared logic refers to methods that provide common functionality across the application, typically grouped under a single class. These methods don’t rely on instance-specific data.

#### Example: Shared Date and Time Operations
```typescript
import * as moment from 'moment';

class DateTimeUtils {
    // Calculate duration in minutes between two dates
    static calculateDuration(startDate: string, endDate: string): number {
        const start = moment(startDate);
        const end = moment(endDate);
        return Math.abs(end.diff(start, 'minutes'));
    }

    // Format a date to a common format
    static formatToCommonDate(date: string): string {
        return moment(date).format("YYYY-MM-DD HH:mm:ss");
    }
}

// Usage
const start = "2024-12-30T08:00:00";
const end = "2024-12-30T10:30:00";

console.log(`Duration: ${DateTimeUtils.calculateDuration(start, end)} minutes`);
console.log(`Formatted Date: ${DateTimeUtils.formatToCommonDate(start)}`);
```

---

### **3. Factory Methods**
Factory methods are static methods used to create and initialize objects of a class. They encapsulate object creation logic, making it easier to manage and reuse.

#### Example: Factory Method for Creating Instances
```typescript
class User {
    constructor(public username: string, public email: string, public role: string) {}

    // Factory method to create a User instance with default role
    static createUser(username: string, email: string): User {
        return new User(username, email, "User");
    }

    // Factory method to create an Admin
    static createAdmin(username: string, email: string): User {
        return new User(username, email, "Admin");
    }
}

// Usage
const user = User.createUser("john_doe", "john.doe@example.com");
console.log(`User: ${user.username}, Role: ${user.role}`);

const admin = User.createAdmin("admin_01", "admin@example.com");
console.log(`Admin: ${admin.username}, Role: ${admin.role}`);
```

---

### **Summary of Key Points**
- **Utility Functions**:
  - Provide specific functionality like hashing, encryption, or formatting.
  - Example: Password hashing or number formatting.

- **Shared Logic**:
  - Encapsulate operations that are reused across the application but don’t depend on instance data.
  - Example: Calculating time durations or formatting dates.

- **Factory Methods**:
  - Simplify object creation and initialization with pre-defined defaults or configurations.
  - Example: Creating `User` or `Admin` instances with a factory method.

By combining these approaches, you create modular, reusable, and maintainable code that adheres to good design principles.



### Object-Oriented Programming (OOP):
OOP is a programming paradigm based on the concept of **objects**, which can contain **data** (attributes or properties) and **methods** (functions) that operate on the data. OOP promotes modularity, reusability, and maintainability by organizing code into classes and objects. 

**Key principles of OOP:**
1. **Encapsulation**: Wrapping data and methods into a single unit (class) and restricting direct access to some components using access modifiers (e.g., private, protected).
2. **Inheritance**: Allowing a class (child) to inherit properties and behavior from another class (parent), promoting code reuse.
3. **Polymorphism**: Enabling objects to take on multiple forms, such as method overloading (compile-time) and method overriding (runtime).
4. **Abstraction**: Hiding implementation details and showing only the essential features of an object.

---

### Difference Between Abstract Class and Interface:
| **Aspect**               | **Abstract Class**                                                                                 | **Interface**                                                                                 |
|--------------------------|----------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|
| **Definition**           | A class that can have both abstract (unimplemented) and concrete (implemented) methods.           | A blueprint for a class that only contains method signatures (no implementation).           |
| **Purpose**              | Used for sharing behavior (via implemented methods) and defining a contract.                      | Used purely to define a contract for classes to follow.                                     |
| **Inheritance**          | A class can inherit only one abstract class (single inheritance).                                  | A class can implement multiple interfaces (multiple inheritance).                           |
| **Methods**              | Can have implemented (concrete) and unimplemented (abstract) methods.                             | Contains only abstract method signatures; no method implementations.                       |
| **Fields/Properties**    | Can include fields, constants, and properties with access modifiers.                               | Can only include constants (no fields or instance variables).                              |
| **Default Implementation** | Supports default behavior in methods.                                                            | Requires implementation of all methods in the implementing class unless defaults are provided (in some languages like Java 8+). |
| **Usage Example (Java)** | `abstract class Shape { abstract void draw(); }`                                                  | `interface Drawable { void draw(); }`                                                      |
| **Real-world Use Case**  | When you need shared logic between multiple related classes.                                       | When you need to ensure a contract is followed by unrelated classes.                       |

### Choosing Between Abstract Class and Interface:
- Use an **abstract class** when:
  - Classes share common functionality that you want to implement in a base class.
  - You want to take advantage of single inheritance for tightly related classes.

- Use an **interface** when:
  - You need to define a common contract for unrelated classes.
  - You want to support multiple inheritance for a class.
