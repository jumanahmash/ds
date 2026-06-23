# Student Advising System

A comprehensive Java-based academic management platform developed as a course project for **CSC 212: Data Structures** at the **College of Computer and Information Sciences, King Saud University** (**Spring 2026**) . 

The system simulates a real-world software evolution scenario, transitioning from foundational linear data structures to highly optimized non-linear structures to handle student records, advising appointments, and workshops efficiently.

---

## 🚀 Project Overview

The **Student Advising System** is designed to assist academic advisors in managing student profiles and scheduling critical academic events. The system enforces strict architectural rules such as conflict-free scheduling, structural immutability for key fields, and automated cascade operations upon data deletion.

### Key Features
* **Student Record Management:** Full CRUD capabilities including adding unique records, comprehensive updating, and secure deletion[cite: 10, 30].
* [**Advanced Search Filters:** Search and filter students by ID, exact full name, case-insensitive partial name, email, major, and academic year level.
* **Event Scheduling Subsystem:** Seamless allocation of one-on-one `Meetings` (exactly one student) and multi-participant `Workshops`
* **Automated Cascade Deletion:** Removing a student automatically purges their individual meetings, retracts their registration from workshops, and completely deletes any workshop left with zero participants.
* **Data Initialization via CSV:** Supports bulk importing of initial datasets from external data sheets (`students_100.csv` and `events_40.csv`).

---

## 🛠️ System Architecture & Data Structures

To comply with academic constraints, **no built-in collections from `java.util` (such as `ArrayList`, `LinkedList`, `Stack`, or `Queue`) were used**. All data structures were engineered completely from scratch.

### Phase 1: Linear Data Structures
The initial phase focused on building operational logic using foundational linear collections, operating at a worst-case time complexity of $O(n)$ for search and sequential tracking:
1. **Custom Linked List (`CustomLinkedList`):** Used to store the master inventory of events and maintain sorted records.
2. **Custom Stack (`CustomStack`):** Integrated to support historical state tracking, log tracking, or rollback/undo operations for data mutations.
3. **Custom Queue (`CustomQueue`):** Employed to manage chronological event parsing and workshop registration waitlists sequentially.

### Phase 2: Non-Linear Optimization (BST Implementation)
To handle enterprise-scale loads, Phase 2 refactored the core storage tier to utilize hierarchical data structures:
* **Binary Search Tree (`StudentBST`):** Student profiles are indexed and stored inside a BST sorted by their unique `studentId`. This migration optimized search, insertion, and retrieval operations from a linear scan $O(n)$ to an average time complexity of $O(\log n)$

---

## 📋 Technical Constraints & Rules

* **Immutability:** Student IDs and scheduled event timestamps are entirely immutable once instantiated via constructors to preserve transactional integrity.
* [cite_start]**Conflict Prevention:** The system cross-references active time-slots within the data structures to block overlapping meetings or workshops for any participating student.
* **Chronological Ordering:** Sequential data comparisons and structural indexing rely directly on implementing Java’s standard `Comparable` interface.

---

## 💻 Class Structure Overview

* **`Student` / `IPerson`**: Represents individuals within the system, encapsulating names, distinct IDs, emails, majors, and specific year levels
* **`Event` / `Meeting` / `Workshop`**: Academic event abstractions implementing specific occupancy and relationship logic
* **`AdvisingSystem`**: The orchestrator engine coordinating operations between custom collections, file I/O operations, and menu-driven interfaces

---

## 🏁 How to Run the Application

1. **Clone the Repository:**
   ```bash
   git clone [https://github.com/your-username/student-advising-system.git](https://github.com/your-username/student-advising-system.git)
   cd student-advising-system
