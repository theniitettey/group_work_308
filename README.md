# Atinka Meds Pharmacy Inventory System

## Project Overview

This system Inventory System is a terminal-based application developed for **Atinka Meds**, a community pharmacy in Adenta, Accra. This system digitizes pharmacy operations with an offline-first approach to accommodate unreliable internet connectivity.

Key features include drug inventory management, supplier relationships, purchase history tracking, and stock monitoring, all implemented using custom data structures and algorithms—**no external libraries required**. Data is persisted locally for reliability, and a menu-driven interface ensures ease of use for pharmacists.

---

## Features

- **Drug Management:** Add, remove, update, and list drugs with details (name, code, suppliers, expiration date, price, stock level).
- **Search & Sort:** Binary search by drug name/code; sort drugs alphabetically or by price using custom merge sort.
- **Supplier Mapping:** Bidirectional drug-supplier relationships; filter suppliers by location or delivery time.
- **Purchase History:** Log transactions (drug code, quantity, timestamp, buyer ID, total cost) in a custom linked list, sortable by timestamp.
- **Stock Monitoring:** Track low stock levels using a custom min-heap, prioritizing drugs with lowest quantities.
- **File Persistence:** Store data in local `.dat` files for offline reliability.
- **Menu-Driven Interface:** Intuitive terminal interface for all operations.

---

## System Architecture

The system is modular, with clear separation of concerns:

- **Model Classes (`model/`):**

  - `Drug.java`: Drug entity (code, name, stock level)
  - `Supplier.java`: Supplier details (ID, name, delivery time)
  - `Transaction.java`: Purchase details (drug code, timestamp)

- **Data Structures (`datastructures/`):**

  - `MinHeap.java`: Custom min-heap for stock monitoring
  - `LinkedList.java`: Custom linked list for purchase history

- **Services (`services/`):**

  - `DrugManager.java`: Drug CRUD, search, sorting
  - `SupplierManager.java`: Supplier data, relationships
  - `PurchaseManager.java`: Purchases and sales history
  - `StockMonitor.java`: Stock level monitoring

- **Persistence (`persistence/`):**

  - `FilePersistence.java`: File I/O for data persistence

- **UI (`ui/`):**

  - `MenuInterface.java`: Terminal-based user interface

- **Entry Point:**
  - `Main.java`: Initializes components and starts the application

---

## File Structure

```
PharmacyInventorySystem/
├── src/
│   ├── model/
│   │   ├── Drug.java
│   │   ├── Supplier.java
│   │   └── Transaction.java
│   ├── datastructures/
│   │   ├── MinHeap.java
│   │   └── LinkedList.java
│   ├── services/
│   │   ├── DrugManager.java
│   │   ├── SupplierManager.java
│   │   ├── PurchaseManager.java
│   │   └── StockMonitor.java
│   ├── persistence/
│   │   └── FilePersistence.java
│   ├── ui/
│   │   └── MenuInterface.java
│   └── Main.java
├── data/
│   ├── drugs.dat
│   ├── suppliers.dat
│   ├── supplier_drugs.dat
│   ├── drug_suppliers.dat
│   └── purchases.dat
├── README.md
```

- **src/**: Java source code, organized by functionality
- **data/**: Persistent data files:
  - `drugs.dat`: Drug details
  - `suppliers.dat`: Supplier details
  - `supplier_drugs.dat`: Supplier-to-drug mappings
  - `drug_suppliers.dat`: Drug-to-supplier mappings
  - `purchases.dat`: Transaction log

---

## Setup Instructions

1. **Ensure Java is Installed:**  
    Verify JDK installation:

   ```sh
   java -version
   javac -version
   ```

2. **Organize Source Files:**  
   Place Java source files in the respective `src/` subdirectories.

3. **Compile the Project:**

   ```sh
   cd PharmacyInventorySystem/src
   javac Main.java model/*.java datastructures/*.java services/*.java persistence/*.java ui/*.java
   ```

4. **Run the Application:**
   ```sh
   java Main
   ```

---

## Usage

The application launches a menu-driven terminal interface with options to:

- **Add Drug:** Enter drug details (code, name, suppliers, expiration date, price, stock level)
- **Remove Drug:** Remove by code
- **Update Drug:** Edit name, price, or stock level
- **List Drugs:** Display all drugs
- **Search Drug by Code:** O(1) hash table lookup
- **Search Drug by Name:** O(log n) binary search
- **Sort Drugs by Name/Price:** O(n log n) merge sort
- **Add Supplier:** Add supplier (ID, name, contact, location, delivery time)
- **Filter Suppliers:** By location or delivery time
- **Add Purchase:** Record purchase (drug code, quantity, buyer ID, total cost)
- **View Recent Purchases:** Display recent purchases for a drug
- **Check Low Stock:** List drugs below stock threshold (min-heap)
- **Exit:** Close application

Data is automatically saved to the `data/` directory after each operation.

---

## Data Structures & Algorithms

- **Hash Tables:** O(1) lookups (drugs, suppliers, relationships)
- **Min-Heap:** O(log n) for stock monitoring
- **Linked List:** O(1) append for purchase history
- **Sorted Array:** O(log n) binary search, O(n log n) merge sort
- **File I/O:** O(n) for reading/writing `.dat` files

---

## Performance Analysis

- **Lookups:** O(1) via hash tables
- **Search:** O(log n) binary search
- **Sorting:** O(n log n) merge sort
- **Stock Monitoring:** O(log n) min-heap insert/update, O(1) peek
- **Space Complexity:** O(n + m + r)  
   _(n = drugs, m = suppliers, r = relationships)_

---

## Design Trade-offs

- **Memory vs. Time:** Multiple hash tables for fast access, higher memory usage
- **Complexity vs. Performance:** Bidirectional mappings enable O(1) queries
- **Flexibility vs. Simplicity:** Multi-index system supports diverse queries

---

## Group Members

| Name            | Activities                                       | % Contribution | Attendance |
| --------------- | ------------------------------------------------ | -------------- | ---------- |
| [Member 1 Name] | Implemented DrugManager, binary search, UI       | 25%            | 90%        |
| [Member 2 Name] | Developed MinHeap, StockMonitor, persistence     | 25%            | 85%        |
| [Member 3 Name] | Designed SupplierManager, relationship mapping   | 20%            | 80%        |
| [Member 4 Name] | Implemented PurchaseManager, merge sort, testing | 20%            | 90%        |
| [Member 5 Name] | Documentation, testing, coordination             | 10%            | 95%        |

_Replace placeholders with actual member details._

---

## How to Add Issues

To report bugs, request features, or suggest improvements:

1. **Go to the GitHub repository** for this project.
2. Click on the **"Issues"** tab.
3. Click **"New Issue"** and select the appropriate template (bug, feature, etc.).
4. Fill in the details, including steps to reproduce (if applicable), expected behavior, and screenshots if helpful.
5. Submit the issue.  
   _The team will review and respond as soon as possible._

---

## License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT):

```
MIT License

Copyright (c) 2024 Atinka Meds Pharmacy

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
