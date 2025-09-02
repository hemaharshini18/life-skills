# SOLID Principles in Python 

## Introduction
In software engineering, **loose coupling** is crucial. Loosely coupled classes minimize dependencies, reduce risks of changes breaking unrelated parts of the system, and enhance **reusability**. The SOLID principles serve as a design compass, enabling developers to write software that is easy to maintain, extend, and scale.

The principles are:
- **S** – Single Responsibility Principle (SRP)
- **O** – Open/Closed Principle (OCP)
- **L** – Liskov Substitution Principle (LSP)
- **I** – Interface Segregation Principle (ISP)
- **D** – Dependency Inversion Principle (DIP)

---

## 1. Single Responsibility Principle (SRP)
### Definition
A class should have **only one reason to change**, meaning each class should focus on a **single purpose**.

### Real-Life Example: The Bakery
In a bakery, if a single baker handles baking, inventory, ordering, customer service, and cleaning, productivity suffers. Instead, each role should be separated.

### Python Example
```python
# Class for baking bread
class BreadBaker:
    def bakeBread(self):
        print("Baking high-quality bread...")

# Class for managing inventory
class InventoryManager:
    def manageInventory(self):
        print("Managing inventory...")

# Class for ordering supplies
class SupplyOrder:
    def orderSupplies(self):
        print("Ordering supplies...")

# Class for serving customers
class CustomerService:
    def serveCustomer(self):
        print("Serving customers...")

# Class for cleaning the bakery
class BakeryCleaner:
    def cleanBakery(self):
        print("Cleaning the bakery...")

# Usage
def main():
    baker = BreadBaker()
    inventoryManager = InventoryManager()
    supplyOrder = SupplyOrder()
    customerService = CustomerService()
    cleaner = BakeryCleaner()

    baker.bakeBread()
    inventoryManager.manageInventory()
    supplyOrder.orderSupplies()
    customerService.serveCustomer()
    cleaner.cleanBakery()

if __name__ == "__main__":
    main()
```
Each class is responsible for a single task, ensuring clarity and maintainability.

---

## 2. Open/Closed Principle (OCP)
### Definition
Software entities should be **open for extension but closed for modification**.

### Real-Life Example: Payment Processing
Initially, a store supports only **credit card payments**. Later, it needs to support **PayPal** without changing the original class.

### Python Example
```python
from abc import ABC, abstractmethod

# Base class for payment processing
class PaymentProcessor(ABC):
    @abstractmethod
    def processPayment(self, amount):
        pass

class CreditCardPaymentProcessor(PaymentProcessor):
    def processPayment(self, amount):
        print(f"Processing credit card payment of ${amount}")

# Extension without modifying original code
class PayPalPaymentProcessor(PaymentProcessor):
    def processPayment(self, amount):
        print(f"Processing PayPal payment of ${amount}")

# Usage
def processPayment(processor, amount):
    processor.processPayment(amount)

def main():
    creditCardProcessor = CreditCardPaymentProcessor()
    payPalProcessor = PayPalPaymentProcessor()

    processPayment(creditCardProcessor, 100.00)
    processPayment(payPalProcessor, 150.00)

if __name__ == "__main__":
    main()
```
New payment methods can be added without modifying existing ones.

---

## 3. Liskov Substitution Principle (LSP)
### Definition
Subtypes must be **substitutable for their base types** without altering correctness.

### Real-Life Example: Rectangle vs. Square
A square is a special rectangle, but substituting it in all contexts may break logic.

### Python Example
```python
# Base class for shapes
class Rectangle:
    def __init__(self, w, h):
        self.width = w
        self.height = h

    def area(self):
        return self.width * self.height

    def setWidth(self, w):
        self.width = w

    def setHeight(self, h):
        self.height = h

# Square overrides behavior
class Square(Rectangle):
    def __init__(self, size):
        super().__init__(size, size)

    def setWidth(self, w):
        self.width = self.height = w
```
While functional, substituting `Square` for `Rectangle` may break logic where width and height are expected to change independently.

---

## 4. Interface Segregation Principle (ISP)
### Definition
Clients should not be forced to depend on **interfaces they don’t use**.

### Real-Life Example: Restaurant Menu
A vegetarian customer should not be forced to see non-vegetarian options.

### Python Example
```python
from abc import ABC, abstractmethod

class IVegetarianMenu(ABC):
    @abstractmethod
    def getVegetarianItems(self):
        pass

class INonVegetarianMenu(ABC):
    @abstractmethod
    def getNonVegetarianItems(self):
        pass

class IDrinkMenu(ABC):
    @abstractmethod
    def getDrinkItems(self):
        pass

class VegetarianMenu(IVegetarianMenu):
    def getVegetarianItems(self):
        return ["Vegetable Curry", "Paneer Tikka", "Salad"]

class NonVegetarianMenu(INonVegetarianMenu):
    def getNonVegetarianItems(self):
        return ["Chicken Curry", "Fish Fry", "Mutton Biryani"]

class DrinkMenu(IDrinkMenu):
    def getDrinkItems(self):
        return ["Water", "Soda", "Juice"]

# Usage
def displayVegetarianMenu(menu):
    print("Vegetarian Menu:")
    for item in menu.getVegetarianItems():
        print(f"- {item}")
```
Each interface is lean, avoiding irrelevant methods.

---

## 5. Dependency Inversion Principle (DIP)
### Definition
High-level modules should depend on **abstractions, not concrete implementations**.

### Real-Life Example: Version Control Systems
A development team uses an abstract VCS (e.g., Git), without depending on its internal details.

### Python Example
```python
from abc import ABC, abstractmethod

class IVersionControl(ABC):
    @abstractmethod
    def commit(self, message): pass

    @abstractmethod
    def push(self): pass

    @abstractmethod
    def pull(self): pass

class GitVersionControl(IVersionControl):
    def commit(self, message):
        print(f"Committing changes with message: {message}")

    def push(self):
        print("Pushing changes to remote repository.")

    def pull(self):
        print("Pulling changes from remote repository.")

class DevelopmentTeam:
    def __init__(self, vc: IVersionControl):
        self.versionControl = vc

    def makeCommit(self, message):
        self.versionControl.commit(message)

    def performPush(self):
        self.versionControl.push()

    def performPull(self):
        self.versionControl.pull()

# Usage
def main():
    git = GitVersionControl()
    team = DevelopmentTeam(git)

    team.makeCommit("Initial commit")
    team.performPush()
    team.performPull()

if __name__ == "__main__":
    main()
```
This ensures the team depends on an **interface**, not a specific implementation.

---

## Need for SOLID Principles in OOP
- **Maintainability** – Changes are localized and easier to implement.
- **Scalability** – Features can be added without breaking existing code.
- **Flexibility** – Abstractions allow smooth swapping of implementations.
- **Stability** – Loosely coupled systems minimize ripple effects.

---

## Conclusion
The SOLID principles act as a guiding framework for **object-oriented design** in Python. By applying them consistently, developers can build systems that are **clean, extensible, testable, and maintainable**, reducing technical debt and enabling long-term growth.

---

## References
1. GeeksforGeeks – [SOLID Principles in Programming](https://www.geeksforgeeks.org/system-design/solid-principle-in-programming-understand-with-real-life-examples/)
2. Robert C. Martin – [Bob Martin SOLID Principles of Object Oriented and Agile Design](https://www.youtube.com/watch?v=TMuno5RZNeE)
