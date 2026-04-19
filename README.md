# 🏥 Hospital Management Ontology

An OWL-based ontology developed using **Protégé** to model a hospital
management system. This ontology represents real-world healthcare
concepts including Patients, Doctors, Diagnoses, and Treatments,
with subclass hierarchies, object properties, data properties,
and SPARQL query support.

---

## 📋 Overview

| Property        | Detail                        |
|-----------------|-------------------------------|
| **Author**      | Your Name                     |
| **Student ID**  | Your Student ID               |
| **Module**      | Semantic Web Technologies     |
| **Institution** | SETU                          |
| **Tool**        | Protégé 5.x                   |
| **Language**    | OWL 2 (Web Ontology Language) |
| **Namespace**   | http://example.org/hospital#  |

---

## 🏗️ Ontology Structure

### Classes

| Class        | Description                             |
|--------------|-----------------------------------------|
| `Patient`    | A person receiving medical care         |
| `Doctor`     | A medical professional                  |
| `Diagnosis`  | A medical condition identified          |
| `Treatment`  | A medical intervention applied          |
| `Medication` | Subclass of Treatment — drug-based care |
| `Surgery`    | Subclass of Treatment — procedural care |

### Object Properties

| Property       | Domain  | Range     | Description                        |
|----------------|---------|-----------|------------------------------------|
| `hasDiagnosis` | Patient | Diagnosis | Links a patient to their diagnosis |
| `receives`     | Patient | Treatment | Links a patient to their treatment |
| `treatedBy`    | Patient | Doctor    | Links a patient to their doctor    |

### Data Properties

| Property               | Domain    | Type   | Description                    |
|------------------------|-----------|--------|--------------------------------|
| `name`                 | Patient   | String | Full name of the patient       |
| `diagnosisDescription` | Diagnosis | String | Description of the diagnosis   |
| `treatmentName`        | Treatment | String | Name of the treatment applied  |

---

## 👥 Individuals

### Patients

| Individual     | name        | hasDiagnosis        | receives            |
|----------------|-------------|---------------------|---------------------|
| `patient_John` | John Murphy | diag_Hypertension   | med_BloodPressure   |
| `patient_Mary` | Mary OBrien | diag_Migraine       | surg_MRI            |
| `patient_Ali`  | Ali Hassan  | diag_Headache       | med_HeadacheRelief  |

### Diagnoses

| Individual          | diagnosisDescription          |
|---------------------|-------------------------------|
| `diag_Hypertension` | High blood pressure condition |
| `diag_Migraine`     | Chronic migraine condition    |
| `diag_Headache`     | Common headache condition     |

### Treatments

| Individual           | Class      | treatmentName              |
|----------------------|------------|----------------------------|
| `med_BloodPressure`  | Medication | Blood Pressure Medication  |
| `med_HeadacheRelief` | Medication | Headache Relief Medication |
| `surg_MRI`           | Surgery    | MRI Scan                   |

---

## 🔗 Ontology Design Decisions

- **Medication** and **Surgery** are modelled as subclasses of **Treatment**
  because they represent two fundamentally different methods of treating a
  patient — drug-based vs. procedural. This subclass hierarchy enables the
  reasoner to classify treatments automatically and supports more specific
  queries (e.g. find all surgical treatments only).

- **Disjointness** has been applied between `Medication` and `Surgery` since
  a treatment cannot be both a medication and a surgery simultaneously.

- A **cardinality restriction** (`receives min 1 Treatment`) has been applied
  to the `Patient` class to ensure every patient must receive at least one
  treatment, reflecting real-world clinical requirements.

---

**Raw OWL file:**

```
https://raw.githubusercontent.com/kazimdalwakil/hospital-ontology/refs/heads/main/hospital.owl
```

**GitHub Pages:**

```
https://kazimdalwakil.github.io/hospital-ontology/
```

---

## 📁 Repository Structure

```
hospital-ontology/
├── hospital.owl   ← Main ontology file (OWL 2)
└── README.md      ← Project documentation
```

## How to Use
- Download the .owl file and open in Protégé
- Run HermiT reasoner to check consistency
- Use the SPARQL tab to query patient data
---

## 🔗 Reuse & Linked Data

This ontology is publicly available and can be reused by:

* Healthcare information systems needing a base patient–treatment model
* Academic projects exploring semantic web technologies
* Developers extending hospital data models with additional classes
---

## 🛠️ Built With

* Protégé — Ontology editor
* OWL 2 — Web Ontology Language
* HermiT Reasoner — OWL reasoner
* SPARQL — Query language for RDF
---

## 📄 License

This project is submitted as part of academic coursework at SETU.
For reuse or extension, please credit the original author.

