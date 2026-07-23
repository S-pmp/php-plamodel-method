# SPEC Appendix

## Purpose

PMP (php-plamodel-method) is a structural framework designed to achieve  
**outer fixation × 10 grammar actions × unified logic**.

Its purpose is to fully separate the UI layer, grammar layer, and logic layer,  
providing a dependency-free, secure, and extensible application structure.

This appendix supplements the intent and design philosophy of the outer OS.

---

## Glossary

### parts  
UI layer.  
A simple component that calls the outer grammar.  
No logic is written here.

### model  
Grammar layer.  
Receives requests from **parts** and passes them to **core**.

### core  
Logic layer.  
The only place where processing is implemented.  
Protecting this layer ensures the safety of the entire application.

### Zero Dependency  
A structure that does not rely on external libraries or frameworks.  
This minimizes attack surface and strengthens security.

### Outer OS  
A structure that fixes the three layers (parts/model/core) from the outside  
to keep logic safe.  
UI, grammar, and logic are fully separated and operate without dependencies.

### Black Box (core.php)  
A structure that completely hides logic from the outside.  
By unifying processing in **core.php**, the outer OS ensures safety and extensibility.

### Translation Dictionary (model.php)  
A layer that converts requests from **parts** into a form that **core** can understand.  
It connects the 10 grammar actions with the internal logic.

### Outer Fixation  
A design philosophy that fixes the UI, grammar, and logic layers from the outside  
to maintain structural consistency and logic safety.

### Grammar 10 Actions  
The minimal operational units provided by the outer OS:  
**query / filter / sort / render / authenticate / save / update / delete / route / notify**

### parts/home.php (UI Layer)  
Entry point of the outer OS.  
Receives user actions and delegates processing to **model**.  
No logic is written here.

### model/home.php (Grammar Layer / Translation Dictionary)  
Converts requests from **parts** into a format that **core** can understand.  
Uses the 10 grammar actions to pass processing to **core**.

### core/home.php (Logic Layer / Black Box)  
The only place where processing is implemented.  
Completely hidden from the outside.  
Protecting this layer ensures the safety of the entire application.

These three layers together establish:

- Outer Fixation  
- Unified Grammar (10 Actions)  
- Single Logic (Black Box)

This forms the minimal structure of PMP.

---

## Minimal Example

The minimal structure of PMP consists of three files:

- **parts/home.php** – UI layer that receives user actions and calls the outer grammar  
- **model/home.php** – grammar layer that translates requests using the 10 actions  
- **core/home.php** – logic layer (black box) where all processing is implemented

Together, these three files establish the smallest possible implementation of the outer OS:
a fixed UI, a unified grammar, and a single protected logic layer.

---

## Flow

The outer OS of PMP consists of three layers:  
**parts (UI) → model (grammar) → core (logic)**.

1. **parts** receives user actions and delegates processing to **model**.  
2. **model** translates the request using the 10 grammar actions and passes it to **core**.  
3. **core** performs the processing as the only logic implementation layer and returns the result.

This flow ensures complete separation of UI, grammar, and logic,  
establishing outer fixation, unified logic, and zero dependency.

> ※ This appendix describes only the outer structure (parts/model/core layering and minimal examples).  
> It does not include any internal logic or implementation details.  
> The core/server logic remains private and is not part of this document.

---

## Appendix

- [Purpose](#purpose)
- [Glossary](#glossary)
- [Minimal Example](#minimal-example)
- [Flow](#flow)
