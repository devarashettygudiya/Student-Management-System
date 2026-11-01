# Student Management System (Java)

A menu-driven console application to manage student records, marks, grades and class statistics. Data is saved to `students.txt` so it persists between runs.

## How to Run
```
javac *.java
java Main
```
Requires JDK 8 or higher.

## Features
1. Add, view, update and delete students
2. Search by ID or by name (partial match)
3. Add / update subject-wise marks (validated 0-100)
4. Automatic average and grade calculation
5. Sort by name or by average
6. Class statistics: class average, topper, grade distribution chart
7. Printable report card per student
8. Auto-save / auto-load using file handling

## Project Structure
| File | Purpose |
|---|---|
| `Main.java` | User interface (menu, input handling) |
| `StudentManager.java` | Business logic (add, search, sort, statistics) |
| `Student.java` | Student entity (extends Person, implements Gradable) |
| `Person.java` | Abstract parent class |
| `Gradable.java` | Interface for grading behaviour |
| `FileHandler.java` | Saving and loading data |
| `InvalidInputException.java` | Custom exception for bad input |
| `StudentNotFoundException.java` | Custom exception for missing ID |

## Java Concepts Demonstrated
| Concept | Where |
|---|---|
| Classes and Objects | `Student`, `StudentManager` |
| Encapsulation | Private fields with getters/setters in `Person`, `Student` |
| Inheritance | `Student extends Person` |
| Abstraction | Abstract class `Person`, interface `Gradable` |
| Polymorphism | `@Override` of `getRole()`, `getGrade()`, `toString()` |
| Collections | `ArrayList`, `LinkedHashMap`, `TreeMap` |
| Sorting | `Comparator` in `StudentManager` |
| Exception handling | Custom exceptions, try/catch, multi-catch, try-with-resources |
| File I/O | `BufferedReader` / `BufferedWriter` in `FileHandler` |
| Control flow | `switch`, `do-while`, `for`, `while` |
| Input validation | `readInt`, `readNonEmpty`, email and marks checks |
| Separation of concerns | UI (`Main`) vs logic (`StudentManager`) vs storage (`FileHandler`) |

## Grading Scale
| Average | Grade |
|---|---|
| 90+ | A+ |
| 80-89 | A |
| 70-79 | B |
| 60-69 | C |
| 50-59 | D |
| Below 50 | F |

## Possible Viva Questions
- **Why is `Person` abstract?** We never create a plain Person; it holds shared data and forces subclasses to define `getRole()`.
- **Difference between abstract class and interface?** Abstract classes can hold state and constructors; interfaces define a behaviour contract a class promises to follow.
- **Why custom exceptions?** They give clear, meaningful error messages for our own rules (duplicate ID, bad marks).
- **Why `LinkedHashMap` for marks?** It keeps subjects in the order they were entered.
- **Why try-with-resources?** It closes files automatically, even if an error occurs.
- **Where is polymorphism used?** Overridden methods like `getGrade()` and `toString()`; `Student` can be treated as a `Person` or `Gradable`.
- **Future improvements:** add `Teacher extends Person`, a database (JDBC), or a GUI (Swing/JavaFX).
