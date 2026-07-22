# Architecture Overview (Outer OS Structural Philosophy)

The Outer OS is designed to maximize application safety, extensibility, and structural consistency.  
It is built on three core principles:

**Outer Fixation × Grammar 10 Actions × Black Box Logic**

This document summarizes the architectural philosophy adopted by PMP (php-plamodel-method).  
While the README serves as the entry point, the SPEC_APPENDIX defines the specification,  
the Overview illustrates the structure, and the Compatibility document explains external relations,  
**Architecture.md describes the philosophy of the Outer OS itself.**

---

## 1. Outer Fixation

The central idea of the Outer OS is **Outer Fixation**.

Outer Fixation means fixing the application structure from the outside so that  
the UI, grammar, and logic layers always maintain a consistent shape.

### Why Outer Fixation is necessary

- Logic leaking into the UI causes structural collapse  
- Grammar mixing with logic reduces safety  
- UI touching logic directly increases attack surface  
- External dependencies shorten system lifespan  

Outer Fixation prevents these issues structurally.

### Effects of Outer Fixation

- **Unbreakable structure**  
- **Maximum safety**  
- **Maximum extensibility**  
- **Easy long-term maintenance**  
- **Extended lifespan through zero dependency**

The Outer OS is “a structure designed to protect structure.”

---

## 2. Grammar 10 Actions

The Outer OS standardizes all application behavior into 10 minimal actions:

- query  
- filter  
- sort  
- render  
- authenticate  
- save  
- update  
- delete  
- route  
- notify

---

## Grammar 10 Actions – Roles

- The 10 Actions are defined as the minimal set of operations that can express all outer‑layer behaviors without overlap or omission when decomposing the structure.

- The three‑layer architecture — parts → model → core — separates outer processing from internal logic, creating a structure where the core cannot be accessed directly from the outside.

- The model functions as a “translation dictionary,” converting inputs received by parts into internal representations that the core can understand.

---

## PMP Grammar (10 Actions)

In PMP, the outer structure is decomposed into ten minimal actions, treated as “words.”  
Complex behavior is expressed by chaining these actions together, forming “sentences.”

### **Example (list display)**

query → filter → sort → render


Even complex game logic follows the same grammar.  
For example, attacking an enemy and updating the screen:

### **Example (game action)**

query (get enemy HP) → update (reduce HP) → render (refresh screen) → notify (effect)


Each feature is composed by combining multiple actions.  
Because the same grammar applies to web apps, applications, and games,  
PMP provides a universal outer‑layer structure independent of languages or frameworks.

---

## Role of the Grammar 10 Actions

- Provide a grammar that allows the model to act as a “translation dictionary”  
- Standardize the flow from parts → model → core  
- Break down application behavior into minimal structural units  

---

## Effects of the Grammar 10 Actions

- **Structural consistency**  
- **Standardized processing**  
- **Conflict-free extensibility**  
- **Foundation for unified logic in the core**

The Grammar 10 Actions are the “language” of the Outer OS.


---

## 3. Black Box Logic

`core.php` is the **only** place where logic is implemented.

## Black Box Structure – Roles

- The three‑layer architecture — parts → model → core — separates outer‑layer processing from internal logic, resulting in a structure where the core cannot be accessed directly from the outside.

- The model acts as a “translation dictionary,” converting outer‑layer inputs from parts into internal representations that the core can execute.


### Meaning of the Black Box

- Completely hidden from the outside  
- Not directly accessible from parts or model  
- Internal structure never leaks outward  
- Unified logic maximizes safety  

### Why the Black Box is necessary

- Logic leaking into the UI increases attack surface  
- Logic scattered across multiple locations becomes unmaintainable  
- Exposed logic breaks structural integrity  

### Effects of the Black Box

- **Maximum safety**  
- **Maximum extensibility**  
- **Zero dependency**  
- **Long-term maintainability**

The Black Box is the “heart” of the Outer OS.

---

## 4. Three-Layer Separation

The Outer OS consists of three layers:

### 1. parts (UI)
- Receives user interaction  
- Delegates processing to the grammar layer  
- Contains no logic  
- Entry point of the Outer OS  

### 2. model (Grammar / Translation Dictionary)
- Translates requests from parts into a form the core can understand  
- Uses the Grammar 10 Actions  
- Acts as the “language layer”  

### 3. core (Logic / Black Box)
- The only place where logic is implemented  
- Completely hidden from the outside  
- Center of safety and extensibility

### Note: Model / Core Structure in the Complete Version

This Architecture.md describes the structural philosophy of the Outer OS.
In the complete version, the model layer is divided into two parts:

- **model.php** — the grammar dictionary (translates parts' requests into the 10 grammar actions)
- **model/** — the outer logic layer (the only area where users write their logic)

Additionally, **core is the layer that contains the logic for closing and executing the grammar (10 actions)**,
while outer logic is written in the model/ directory.

Both core and model.php are foundational layers that users do not modify.


### Effects of Three-Layer Separation

- **Complete independence of UI, grammar, and logic**  
- **Structural consistency**  
- **Unbreakable architecture**  
- **Zero dependency**

---

## 5. Zero Dependency

The Outer OS does not rely on external libraries or frameworks.

### Why Zero Dependency matters

- External dependencies shorten lifespan  
- Version updates can break structure  
- Security risks increase  
- Long-term maintenance becomes difficult  

### Effects of Zero Dependency

- **Minimal attack surface**  
- **Easy long-term maintenance**  
- **Structure remains intact**  
- **Outer Fixation becomes possible**

Zero dependency is the “philosophy that extends system lifespan.”

---

## 6. Minimal Example

The minimal structure of the Outer OS consists of three files:

- `parts/home.php`  
- `model/home.php`  
- `core/home.php`  

With these three layers,  
Outer Fixation, unified grammar, and Black Box logic are established.

---

## 7. Why the Outer OS Exists

The Outer OS was created to **solve the structural weaknesses of MVC**.

### Weaknesses of MVC

- Logic easily leaks into the UI  
- Models tend to grow uncontrollably  
- Controllers often hold logic  
- Dependencies accumulate  
- Long-term maintenance becomes difficult  

### Outer OS solutions

- UI contains no logic (parts)  
- Grammar is fixed as a translation dictionary (model)  
- Logic is unified inside a Black Box (core)  
- Grammar 10 Actions unify structure  
- Zero dependency extends lifespan  

The Outer OS is not an evolution of MVC—  
it is **a new architecture designed to protect structure.**

---

## Summary

The Outer OS is “a structure designed to protect structure.”

- Outer Fixation  
- Grammar 10 Actions  
- Unified Black Box logic  
- Three-layer separation  
- Zero dependency  
- Structural resolution of MVC weaknesses  

These principles allow applications to remain safe, unbreakable, and extensible,  
no matter how large they grow.

The Outer OS is a **new architectural philosophy**  
designed to maximize structural safety, extensibility, and lifespan.
