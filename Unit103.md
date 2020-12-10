# 1.03 EHRs and Registries

To allow secondary analysis, the followings are needed:
  * Electronic health records/registries
  * Databases
  * A programming language to navigate through these databases

registries are typically population focused, purpose driven, designed to derive information outcomes defined before data are collected.

EHR: medical histories, demographics, laboratory data and physician notes; may assist with billing, interpractice referrals, appointment scheduling and prescription refills.

EHR 4 core functionalities
  * health information and data
  * results management
  * order entry and support
  * decision support
  
EHRs are patient centric and are designed to collect, share, and use that information for the benefit of that individual.

A patient registry can be a powerful tool to observe the course of disease; to understand variations in treatment and outcomes; to examine factors that influence prognosis and quality of life; to describe care patterns.

Relational database is based on relational algebra

The standard SQL commands are create, select, insert, update, delete, and drop.


```
SELECT columns
FROM table
[WHERE conditions]
[ORDER BY columns];
```

Example:

```
SELECT subject_id, dob
FROM patients
WHERE subject_id = 109
OR subject_id = 117;
```

Complex questions can be answered by joining multiple tables to create a composite result.
Join keywords: INNER JOIN, LEFT JOIN, RIGHT JOIN

Example: INNER JOIN will only return rows where subject_id appears in both the patients table and admissions table

```
SELECT p.subject_id, p.dob, a.hadm_id, a.admittime
FROM patient p
INNER JOIN admission a
ON p.subject_id = a.subject_id
ORDER BY subject_id, hadm_id;
```


## MIMIC III
MIMIC-III is an openly available dataset developed by the MIT lab for computational physiology.
[MIMIC-III paper](http://www.nature.com/articles/sdata201635)

[MIMIC-III Website](http://mimic.physionet.org/mimictables/admissions/)

[Querybuilder](http://mimic.physionet.org/gettingstarted/querybuilder)


# CITI Course

It is a course required to pass before getting approval for accessing MIMIC-III data

## 3 Principles of human research
 * respect of a person
   * inform consent: information, comprehension, and voluntariness 
     * information: research procedure, purposes, risks, anticipated benefits, alternative procedure (e.g., therapeutic treatment if available), and chance to ask questions
 * beneficence
   * rish/benefit assessment
 * justice
   * the selection of subjects of research (not biased toward any minority, race, or a particular group)
   
## History and Ethnics of Human Subjects Research
  * Edward Jenner (1789) ... smallpox vaccine
  * Claude Bernard (1865) ... developed ethical maxim
  * Louise Pasteur (1885) ... rabies vaccine
  * Walter Reed (1900) ... yellow fever vaccine
  * Nuremberg War Crime Trials
  * The Nuremberg Code (1947)
    * A requirement for voluntary consent
    * That the research has scientific merit
    * That the benefits of the research outweigh risks
    * That the subjects have the ability to terminate participation in the research at anytime
  
  
