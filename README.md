# Set Class Implementation (Lab 3) – C++ Console Application

This project implements a **Set class** using a singly linked list in C++. It represents the object‑oriented evolution of the previous two laboratory works, wrapping all set operations into a clean class interface with constructors, methods, and proper encapsulation.

The program generates two sets according to **Variant 25**:
- **Set A** – even numbers.
- **Set B** – numbers divisible by 6.

All elements are two‑digit integers (10–99), and the cardinality of each set varies randomly between **6 and 9** elements per run.

---

## ✨ Features

The `Set` class provides **14 methods** covering creation, inspection, and set‑theoretic operations:

| Method | Description |
|--------|-------------|
| `Set()` | Default constructor – creates an empty set (F1). |
| `Set(n, min, max, type)` | Constructor that generates a set of `n` random numbers satisfying the condition for A or B (F5). |
| `~Set()` | Destructor – frees all allocated memory (F8). |
| `F2()` | Checks whether the set is empty. |
| `F3(value)` | Tests if a given value belongs to the set. |
| `F4(value)` | Inserts a new element at the beginning (no duplicates). |
| `F6()` | Returns the cardinality (size) of the set. |
| `F7(delimiter)` | Returns a string representation with a user‑defined delimiter. |
| `F8()` | Explicitly clears the set and frees memory. |
| `F9(other)` | Checks whether the current set is a subset of `other`. |
| `F10(other)` | Tests whether two sets are equal. |
| `F11(other)` | Returns a new set that is the **union** of the current set and `other`. |
| `F12(other)` | Returns a new set that is the **intersection** of the current set and `other`. |
| `F13(other)` | Returns a new set that is the **difference** (current − `other`). |
| `F14(other)` | Returns a new set that is the **symmetric difference** of the two sets. |

All methods are implemented in a single **header + source** pair, and they are thoroughly tested in the main program.

---

## 🧩 Variant 25 (as assigned)

| Set | Condition                | Example elements |
|-----|--------------------------|------------------|
| A   | Even numbers             | 10, 12, 14, … 98 |
| B   | Multiples of 6           | 12, 18, 24, … 96 |

- **Range:** [10, 99]
- **Cardinality:** 6 … 9 (randomly chosen at each run)
- **Generation:** The parameterized constructor ensures that the requested number of *distinct* elements is created, even if the theoretical maximum is smaller.

---

## 🛠️ Requirements

- C++ compiler with **C++11** support (or later)
- Windows SDK (for `windows.h` – used only to set console output to UTF‑8)
- Standard C++ library

The project is platform‑independent except for the UTF‑8 console setup; on Linux/macOS you can simply remove or comment out the `SetConsoleOutputCP` calls.

---

## 📂 File Structure

```
dsd_lab3.slnx                      # Visual Studio solution file
README.md                            # This file
dsd_lab3/                            # Project folder
├── dsd_lab3.vcxproj                 # Visual Studio project file
├── dsd_lab3.vcxproj.filters         # Project filters (file grouping)
├── OOP_Set_Chernetsov.cpp           # Main program – tests all methods
├── SetLab3_Chernetsov.h             # Header – Set class declaration
└── SetLab3_Chernetsov.cpp           # Implementation of all Set methods
```

---

## 🚀 Building and Running

### Using g++ (MinGW or Linux/macOS)

```bash
g++ -o set_class dsd_lab3/OOP_Set_Chernetsov.cpp dsd_lab3/SetLab3_Chernetsov.cpp -std=c++11
./set_class
```

### Using Visual Studio

1. Open the solution file `dsd_lab3.slnx`.
2. Build the solution (Ctrl+Shift+B).
3. Run (F5).

> ⚠️ On non‑Windows systems, comment out the three lines containing `SetConsoleOutputCP` and `setlocale` in `OOP_Set_Chernetsov.cpp` to avoid compilation errors.

---

## 📊 Example Output

```
Лабораторная работа №3
Вариант 25: А - чётные числа, В - кратные 6
Мощность множеств: 8

Создано множество А: 42 18 76 94 30 52 68 84
Мощность А: 8
Создано множество В: 24 60 36 72 48 12 84 96
Мощность В: 8

F9: A является подмножеством B? Нет
F9: A является подмножеством A? Да

F10: A равно B? Нет
F10: A равно A? Да

F11: Объединение А и В: 42 18 76 94 30 52 68 84 24 60 36 72 48 12 96
Мощность объединения: 15

F12: Пересечение А и В: 84
Мощность пересечения: 1

F13: Разность A - B: 42 18 76 94 30 52 68
Мощность A - B: 7
F13: Разность B - A: 24 60 36 72 48 12 96
Мощность B - A: 7

F14: Симметрическая разность A ∆ B: 42 18 76 94 30 52 68 24 60 36 72 48 12 96
Мощность симметрической разности: 14

Все множества очищены (F8).
```

*Note: Actual numbers will differ due to randomness.*

---

## 📝 Implementation Notes

- **Object‑oriented design** – all operations are now encapsulated in a proper C++ class.
- **RAII principle** – the constructor acquires resources, the destructor releases them automatically.
- **Memory management** – manual `new`/`delete` is used inside the class; no smart pointers (to follow the assignment requirements).
- **Method naming** – original function names (F1…F14) are preserved as method names for consistency with previous labs.
- **Const correctness** – methods that do not modify the object are marked `const`.
- **Efficiency** – because the sets are small (≤9 elements), even O(n²) operations are negligible. The focus is on correctness and clean OOP design.
- **Subset test** – `F9` returns `true` for an empty set, as an empty set is a subset of any set.
- **Union/intersection/difference** – they return new `Set` objects; the original sets remain unchanged.
- **Symmetric difference** – implemented as `(A ∪ B) − (A ∩ B)` using previously defined methods, exactly as required.

---

## 👤 Author

- **Aleksandr Chernetsov**  
  Group: 24VP1  
  Laboratory work for the course *Programming of Dynamic Data Structures*.

---

## 📄 License

This project is created for **educational purposes**. Free use, modification, and distribution are permitted with attribution.
