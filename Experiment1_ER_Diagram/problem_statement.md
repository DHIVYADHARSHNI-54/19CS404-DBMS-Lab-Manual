# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a University Database that manages students, instructors, departments, programs, courses, enrollments, and prerequisites.


## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing Entity-Relationship (ER) diagrams that visually represent the structure and constraints of a real-world database system. It enables effective database planning before implementation.


---

### 🔹 Scenario : University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**

1. Academic programs must be grouped under departments.  
2. Each student should have an admission number, name, date of birth, and contact information.  
3. Instructors must have a staff number, name, and contact information.  
4. Each course must include a course number, name, and number of credits.  
5. The system should track which students enroll in which courses, along with the enrollment date.  
6. Some courses must have prerequisites (i.e., require completion of other courses before enrollment).
---


## 📝 Tasks:

1. Identify all the main entities like Student, Instructor, Course, Program, and Department.  
2. Add important details (attributes) to each entity, like names, IDs, and contact info.  
3. Show how the entities are related (e.g., students enroll in courses, programs belong to departments).  
4. Set rules for how many of each entity can be related (cardinality).  
5. Add prerequisites as a special link between courses.  
6. Draw the ER diagram clearly showing all entities, relationships, and attributes.

# ER Diagram Submission 

NAME - DHIVYA DHARSHNI.B

REGISTER NUMBER - 212223060054

## Scenario Chosen:
University ER Diagram

## ER Diagram:
![dhivya dharshni b universityer drawio](https://github.com/user-attachments/assets/6547cc31-ea19-4cfe-a6bc-f3cb3b554b5a)


## Entities and Attributes:
1.Student - name, phone no., register no., subjects enrolled

2.Department -dept name, dept id

3.Program- program name, program code, courses

4.Course - course code, course name, credits

5.Faculty - name, subject, faculty id

6.University - university name, university id, students and staff

## Relationships and Constraints:
1.Student – Enrollment – Course

        Many-to-Many via Enrollment(Each student can enroll in many courses; each course can have many students)
Participation: Total for Enrollment

2.Department – Program
         One-to-Many(A department offers many programs; each program belongs to one department)

3.Program – Course
         One-to-Many(A program offers many courses; a course belongs to one program)

4.Course – Prerequisite – Course
         Recursive Many-to-Many(A course can have multiple prerequisites; a course can be a prerequisite for multiple other courses)

5.Instructor – Course
         One-to-Many(An instructor can teach multiple courses; each course is taught by one instructor)


## Extension (Prerequisite / Billing):
Modeled with a recursive relationship on the Course entity. Represented by a separate entity Prerequisite with two foreign keys referencing Course.
Ensures that one course must be completed before enrolling in another.Prerequisites are not modeled in the diagram. To add prerequisites: Create a recursive relationship on the Course entity (e.g., prerequisite_for). Billing is also not included.To include billing: Introduce a Billing or Payment entity related to Student and Program/Course, with attributes like amount, due date, status.

## Design Choices:
Entities were selected to reflect distinct real-world components of a university system (e.g., students, faculties, courses). Attributes were chosen based on minimal information needed to identify and manage these entities. Relationships accurately capture the natural hierarchy and many-to-many connections in educational structures. Programs containing multiple courses, and courses being part of multiple programs, support curriculum flexibility. Faculties handle courses, which is a functional and administrative link. The university is at the top of the structure, logically managing both students and faculties.

## RESULT
The ER model captures students, instructors, courses, programs, and their relationships, including enrollments and prerequisites. It’s clear, efficient, and supports future database extensions.
