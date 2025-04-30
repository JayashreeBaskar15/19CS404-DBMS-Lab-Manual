# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

---

## 🧪 Choose One Scenario:

### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

---

### 🔹 Scenario 2: Hospital Database
Design a database for patient management, appointments, medical records, and billing.

**User Requirements:**
- Patient details including contact and insurance.
- Doctors and their departments, contact info, specialization.
- Appointments with reason, time, patient-doctor link.
- Medical records with treatments, diagnosis, test results.
- Billing and payment details for each appointment.

---

## 📝 Tasks:
1. Identify entities, relationships, and attributes.
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3. Include:
   - Cardinality & participation constraints
   - Prerequisites for University OR Billing for Hospital
4. Explain:
   - Why you chose the entities and relationships.
   - How you modeled prerequisites or billing.

# ER Diagram Submission - Student Name

## Scenario Chosen:
University / Hospital (choose one)

## ER Diagram:
![er diagram hospital](https://github.com/user-attachments/assets/9501a0e0-0f49-4b5b-91c7-81982afd97ec)



## Entities and Attributes:
- 1. Patient
Attributes:

Patient_id

Patient_name

DOB

Gender

Address

2. Appointment
Attributes:

Token_no

Time

3. Doctor
Attributes:

Doctor_id

Doctor_name

Phone_no

4. Treatment
Attributes:

Diagonis (should be corrected to "Diagnosis")

Medicine

Test_result

5.Billing
Bill_id
Amount

## Relationships and Constraints:
1. Books
Entities involved: Patient — Appointment

Relationship: A Patient can book one or more Appointments.

Cardinality: One-to-Many (1:N) from Patient to Appointment

Constraint: Each Appointment is booked by exactly one Patient.

2. Conducted by
Entities involved: Appointment — Doctor

Relationship: An Appointment is conducted by a Doctor.

Cardinality: Many-to-One (N:1) from Appointment to Doctor

Constraint: A Doctor can conduct multiple Appointments, but each Appointment is conducted by exactly one Doctor.

3. Visit
Entities involved: Doctor — Treatment

Relationship: A Doctor provides Treatment.

Cardinality: One-to-Many (1:N) from Doctor to Treatment

Constraint: Each Treatment is handled by one Doctor, but a Doctor can handle many Treatments.

4.Pays (First instance):

Connects Doctor to Billing

5.Pays (Second instance):

Connects Treatment to Billing

Implies that billing occurs as a result of treatment.



## Extension (Prerequisite / Billing):
- The Billing entity is linked after the Treatment process:

Once a patient receives treatment, a billing event is triggered.

Billing contains relevant information like:

Bill_id

Amount

Test_result (possibly related to diagnostics/tests done)
## Design Choices:
Entities :
Patient

Central to the healthcare system.

Has personal attributes like name, DOB, gender, address, and a unique identifier (Patient_id).

Assumption: A Patient can book multiple appointments.

Appointment

Represents the scheduling activity.

Attributes like Token_no and Time are specific to an appointment.

Assumption: Each appointment is linked to one patient and one doctor.

Doctor

Key provider of medical services.

Includes identifying and contact information (Doctor_id, Doctor_name, Phone_no).

Assumption: A doctor can conduct many appointments.

Treatment

Represents the outcome or process after a visit.

Includes diagnosis, medicine, and test results.

Assumption: Each treatment is given by a doctor, possibly linked to an appointment (though not shown explicitly).

Relationships :
Books (Patient–Appointment)

Shows that patients initiate appointments.

Reason: Reflects a common hospital workflow where patients book appointments.

Conducted by (Appointment–Doctor)

Associates a doctor with the appointment.

Reason: Each appointment must be handled by one doctor, enabling accountability.

Visit (Doctor–Treatment)

Indicates the doctor administers or supervises treatment.



## RESULT
