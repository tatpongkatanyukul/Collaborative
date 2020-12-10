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

## The Belmont Report: 3 Principles of human research

 * Respect of persons: "To respect autonomy is to give weight to autonomous persons' considered opinions and choices while refraining from obstructing their actions unless they are clearly detrimental to others."
   * inform consent: information, comprehension, and voluntariness 
     * information: research procedure, purposes, risks, anticipated benefits, alternative procedure (e.g., therapeutic treatment if available), and chance to ask questions
 * Beneficence: "The problem posed by these imperatives is to decide when it is justifiable to seek certain benefits despite the risks involved, and when the benefits should be foregone because of the risks."
   * rish/benefit assessment
 * Justice: The principle of justice requires a fair sharing of the burdens and benefits of research and that groups are not exploited because of their circumstances.
   * the selection of subjects of research (not biased toward any minority, race, or a particular group)

These principles "provide an analytical framework that will guide the resolution of ethical problems arising from research involving human subjects" (The National Commission 1979)

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
  * Henry K. Beecher article (1966, 1354-60), Ethics and Clinical Research: unethical research was not confined to Nazi atrocities.
  * US Public Health Service study of untreated syphilis
    * medical research project conducted by the PHS from 1932-1972
    * aka Tuskegee Syphilis Study
    * The study examined the natural course of untreated syphilis in Black American men.
    * The subjects, all impoverished sharecroppers from Macon County, Alabama, were unknowing subjects in the study; they were not told that they had syphilis, nor were they offered effective treatment when it became available in the late 1940s with the advent of penicillin.
    * The study concluded in 1972 when stories about the study appeared in the public press and caused a public outcry.
  * Other abuses: 
    * Willowbrook studies (1956-1970): children with intellectual disabilities were deliberately infected with the hepatitis virus
    * Jewish Chronic Disease Hospital Study (1963): live cancer cells were injected into 22 cognitively impaired patients.
    * prisoner research
  * National Research Act
    * National Commission for the Protection of Human Subjects of Biomedical and Behavior Research ... guidelines
    * Institutional Review Boards (IRBs)
  
  * Application of **Respect for Persons**
    * Informed Consent
    * Privacy
    
  * Application of **Beneficence**
    * Systematic Assessment of Risks and Benefits
    * Minimization of Risk
  
  * Application of **Justice**
    * Selection of Subjects
  
  * General Considerations
    * At times, the principles might come in conflict with each other. 
    * For example, beneficence vs justice: the need to protect children from risk might come in conflict with the need to include children for scientific validity.
    
  * Development of US Regulations (cont.)
    * 45 CFR 46
    * 21 CFR 50 and 56
    * 21 CFR 812 and 312
