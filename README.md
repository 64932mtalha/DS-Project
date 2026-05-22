# 📦 Inventory Management System
A console-based inventory management system built in **C++** using core Data Structures — Linked List and Stack — to manage products, track deletions, and support undo functionality.

---

## 🚀 Features

| Feature | Description |
|--------|-------------|
| ➕ Add Product | Add new products with auto-generated ID |
| 📋 View All | Display full inventory in a formatted table |
| 🔍 Search | Case-insensitive search by name or category |
| ✏️ Update | Edit any product's details by ID |
| 🗑️ Delete | Remove a product (moved to Recycle Bin) |
| ↩️ Undo Delete | Restore the last deleted product |
| ♻️ Recycle Bin | View all deleted products |
| ⚠️ Low Stock | Report products below a stock threshold |

---

## 🏗️ Data Structures Used

### 🔗 Linked List — `LinkedList` class
Used to store the main inventory. Each node holds a `Product`.

- **Insertion** → at the tail (end)
- **Deletion** → by product ID, handles head and middle/tail cases
- **Search** → linear traversal with keyword matching
- **Update** → traverse and modify in-place

### 📚 Stack — `Stack` class
Used as a **Recycle Bin** for deleted products (LIFO).

- **Push** → called when a product is deleted
- **Pop** → called on Undo (restores last deleted product)
- Implemented using a singly linked list of `StackNode`

### 🧮 Search Array — `SearchArray` class
A fixed-size array (max 20) used to temporarily hold search results before displaying them.

---

## 🗂️ Project Structure

```
inventory_system/
│
├── main.cpp          ← All source code (single file)
└── README.md         ← This file
```

---

## 📦 Data Model

```cpp
struct Product {
    int    id;          // Auto-generated unique ID
    string name;        // Product name
    string category;    // Product category
    int    quantity;    // Stock quantity
    float  price;       // Price in Rs
};
```

---

## 🖥️ How to Compile & Run

### Requirements
- C++ compiler (g++ recommended)
- C++11 or later

### Compile
```bash
g++ main.cpp -o inventory
```

### Run
```bash
./inventory        # Linux / macOS
inventory.exe      # Windows
```

---

## 📋 Menu Options

```
┌──────────────────────────────┐
│          MAIN MENU           │
├──────────────────────────────┤
│  1. Add Product              │
│  2. View All Products        │
│  3. Search Product           │
│  4. Update Product           │
│  5. Delete Product           │
│  6. Undo Last Delete         │
│  7. View Recycle Bin         │
│  8. Low Stock Report         │
│  0. Exit                     │
└──────────────────────────────┘
```

---

## 💡 How Key Features Work

### Auto ID Generation
Every new product gets an ID = `max existing ID + 1`, so IDs never repeat even after deletions.

### Search (Case-Insensitive)
Both the keyword and product fields are converted to lowercase before comparison using `tolower()`, so `"phone"` matches `"Phone"` or `"PHONE"`.

### Undo Delete (Stack)
When a product is deleted it is **pushed** onto the Stack (Recycle Bin). Choosing Undo **pops** it off and re-adds it to the Linked List — last deleted is always restored first (LIFO).

### Low Stock Report
Traverses the entire linked list and prints any product whose `quantity` is less than the user-defined threshold (default = 5).

---

## ⚙️ Limitations

- Maximum **20 search results** displayed at a time (SearchArray fixed size).
- Data is **not persisted** — inventory resets on program exit (no file I/O).
- No duplicate ID check on manual restore (Undo always uses the original ID).

---

## 🛠️ Possible Improvements

- [ ] File I/O to save/load inventory from a `.txt` or `.csv` file
- [ ] Sort inventory by price, name, or quantity
- [ ] Expand SearchArray to dynamic size using Linked List
- [ ] Multi-level undo (currently supports single step)
- [ ] Category-wise filtering and reporting

---

## 👨‍💻 Concepts Demonstrated

- `struct` based data modeling
- Singly Linked List (insertion, deletion, traversal)
- Stack using Linked List (push, pop, isEmpty)
- Dynamic memory management (`new`, `delete`)
- String manipulation and case-insensitive search
- Console formatting using `<iomanip>` (`setw`, `setprecision`)

---

*Built as a Data Structures course project demonstrating practical use of Linked List and Stack.*
