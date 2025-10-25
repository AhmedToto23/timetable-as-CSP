# 🧠 Intelligent Systems Project 1
## Automated Timetable Generation as a Constraint Satisfaction Problem (CSP)

### 📘 Overview
This project implements an **automated timetable generator** that models timetable creation as a **Constraint Satisfaction Problem (CSP)**.  
The system dynamically assigns **lectures, rooms, professors, and time slots** while satisfying both **hard** and **soft** constraints to produce an optimal, conflict-free timetable for the CSIT department.

---

### 🎯 Objectives
- Model timetable generation as a **CSP problem**, defining variables, domains, and constraints.
- Build a **solver** capable of producing valid timetables that satisfy all constraints.
- Use **dynamic input data** (from Excel or database sources).
- Provide a **user-friendly interface** for data updates and regeneration of timetables.
- Evaluate performance based on:
  - Constraint violations  
  - Generation time  

---

### 🧩 CSP Formulation

#### **Variables**
Each variable represents a lecture or class session:

**Domain:**  
TimeSlot × Room × Instructor

#### **Domains**
- **Time Slots:** e.g., `Mon 9–10:30`, `Mon 10:45–12:15`
- **Rooms:** `Lab1`, `Lab2`, `Room101`, etc.
- **Instructors:** Faculty members qualified to teach the course.

#### **Constraints**
##### Hard Constraints (must not be violated)
- A professor cannot teach more than one class at the same time.  
- A room cannot host more than one class simultaneously.  
- Each course section must meet its required weekly lectures.  
- Room type must match course type (Lab ↔ Practical, Classroom ↔ Lecture).

##### Soft Constraints (preferred but flexible)
- Minimize student timetable gaps.  
- Avoid early morning or late evening slots.  
- Avoid consecutive lectures in distant rooms for the same instructor.  
- Distribute classes evenly throughout the week.

---

### 📂 Dataset
You can use real or synthetic data extracted from the CSIT department timetable.

| Table | Attributes |
|--------|-------------|
| **Courses** | CourseID, CourseName, Credits, Type (Lecture/Lab) |
| **Instructors** | InstructorID, Name, PreferredSlots, QualifiedCourses |
| **Rooms** | RoomID, Type (Lab/Lecture), Capacity |
| **TimeSlots** | Day, StartTime, EndTime |
| **Sections** | SectionID, Semester, StudentCount |

---

### ⚙️ Implementation Details
- **Language:** Python  
- **Libraries:**  
  - `pandas` → for data handling  
  - `numpy` → for numerical operations  
  - `ortools` (Google CP-SAT Solver) → for CSP solving  
  - `openpyxl` → for Excel file reading/writing  
  - `tkinter` or `streamlit` → for optional GUI (if implemented)

- **Input Files:**  
  CSV/Excel sheets for Courses, Rooms, Instructors, Sections, and TimeSlots

- **Output:**  
  A feasible timetable (printed or exported as `.csv` / `.xlsx`).

---

### 🚀 Running the Project

1. **Install dependencies**
   ```bash
   pip install pandas ortools openpyxl

Place input data
main/
├── Courses.csv
├── Rooms.csv
├── Instructors.csv
├── sections_data.xslx
└── TimeSlots.csv


output
output/
├── timetable_1.csv
├── timetable_2.csv
├── timetable_3_AID
├── timetable_3_CSC
├── timetable_3_CNC
├── timetable_3_BIF
├── timetable_4_AID
├── timetable_4_CSC
├── timetable_4_CNC
└── timetable_4_BIF


📈 Evaluation Metrics

Number of hard constraint violations

Number of soft constraint violations

Total generation time

Schedule fairness across instructors and student sections



