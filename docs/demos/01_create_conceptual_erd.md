# Create a Conceptual ERD

## Background

SD-Med is a small, family-owned doctor's clinic that has been serving the community for over 20 years. The clinic has developed a substantial patient base, but it currently relies on a paper-based system to manage patient records, appointment scheduling, and other operational tasks. Recognizing the need to modernize, SD-Med plans to implement a comprehensive digital database system. This transition aims to enhance operational efficiency, improve data accuracy, and ultimately provide better patient care.

!!! note
    We will only consider entity relationship data modeling concepts for this business scenario and ignore any potential HIPAA or privacy related constraints. Certain aspects of this example have been abbreviated for the purposes of this demo. The scenario is not intended to represent a complete depiction of a real-world medical clinic.

## Business Requirements

After a series of in-depth interviews with staff, owners and doctors, we have identified the following requirements.

- Each **clinic** has employees, such as administrators, nurses, maintenance staff, etc., and an **employee** can only *work at* a single clinic.  
    - Clinic information includes a unique **clinic id**, the **name** of the clinic (used by employees to refer to each location) and **phone**.  
    - Employee information includes a unique **employee id** assigned by the company, **name** (first and last), **address** (street, city, state, and zip), **email**, and **phone** (home and mobile)
- A **doctor** can have multiple **specialties** (there are over 40 different specialties across all doctors that work at the clinic) and information about the doctor includes a unique **doctor id**, and **name** (prefix, first, last, suffix).
- A **patient** must be assigned a *primary* doctor but not all doctors provide primary care.
    - Patient information includes a unique **patient id** assigned by the clinic, **name** (first and last), date of birth (**dob**), **age**, **phone** (home and mobile), and **address** (street, city, state, and zip)
- A patient can *attend* **appointments** with many different specialists, but each appointment is with one doctor at a single clinic.
- A doctor can *hold* many **appointments** with different patients as needed for demand and patient need.
    - A unique **appointment id** is assigned at the time of scheduling for ease of identification since doctor information may not be known and/or can change up until the day of the appointment. Additional information about the appointment include the **appt date time** as well as the **status** (scheduled, completed, cancelled).

### Before Getting Started

1. **Understand the Business Context**: Before jumping into the diagram tool, thoroughly understand the business requirements and make notes of the real-world entities relevant for SD-Med.  
2. **Identify all Entities**: Make note of potential strong and weak entities.  
3. **Consider Relationships**: Identify in the requirements potential relationships that are one-to-one, one-to-many or many-to-many.  
4. **Identify all Attributes**: Make note of simple vs. composite attributes, single vs. multi-valued attributes, if the business requirements referenced any derived attributes as well as any potential key attributes.

??? question "Why are we learning Chen Notation when most ERD tools use Crow's Foot notation?"
    1. Allows you to think more conceptually about the business processes and how they might evolve into a database design.
    2. Forces you to think about the different types of attributes that are required for each entity and how they may be formalized in the design.
    3. **The format does lend itself well to a group project for team building and collaboration.**   

<div style="page-break-after: always;"></div>

## Chen Notation Symbol Quick Reference

![Chen Notation Quick Reference Guide](../assets/screenshots/01_Chen_Notation.png)

## Create New Diagram

Go to [draw.io (app.diagrams.net)](https://app.diagrams.net/).

![New Diagram Default](../assets/screenshots/01_New_Diagram_Default.png)

Click on Change storage and then choose one of the cloud storage options such as Google Drive, OneDrive or Dropbox and authorize the app (if needed).

![New Diagram Cloud](../assets/screenshots/01_New_Diagram_Cloud_Storage.png)   

Click on the blue Create New Diagram button. Give the diagram a meaningful name in the top left, select Blank Diagram and click on Create.
   
![Create Blank Diagram](../assets/screenshots/01_Create_Blank_Diagram.png)

Confirm options and click on Save.

<div style="page-break-after: always;"></div>

??? tip "Tips"
    * Place all entities on the blank diagram first.  
    * Connect entities with their relationships but don’t worry about getting the cardinality correct on the first attempt.  
    * You can always update the cardinality symbols on the relationship lines later.
    * You may find that you need to rearrange the diagram a little so it flows well and you have enough space before adding the attributes to the diagram.  
    * The auto rearrange layout option may not work very well so it is good to do some preliminary organization at this point.  
    * Place all attributes on the diagram first and then connect attributes with their entities.

## Create Entities

Create rectangles for each entity. Be sure to identify any weak entities that are dependent on a strong entity or associative entities. 

In this business scenario, `appointment` could be a weak entity with identifying relationships to `patient`, `doctor`, `clinic`, as well as, `date` and `time`. This presents potential design challenges since changes to the appointment such as doctor reassignment, time and date changes all force primary key changes in `appointment`. The M:N relationship between `patient` and `doctor` is resolved through the `appointment` associate entity.

![Create Entities](../assets/screenshots/01_ERD_Entities.png)

!!! note
    All applicable objects can be found under the Entity Relation Shapes section.

## Create Relationships

Create diamonds for each relationship. Connect entities with their relationship lines and corresponding cardinality (1, M, N). A relationship that is total participation uses double lines but you can always update that later. 

![Create Relationships](../assets/screenshots/01_ERD_Relationships.png)

## Create Attributes

Create ovals for all attributes around the corresponding entity and connect to the entity with a solid line.

![Create Attributes](../assets/screenshots/01_ERD_Attributes.png)

!!! note
    Recall key attributes will have a solid underline whereas a partial key attribute will have a dashed underline, multi-valued attributes will have an oval with double lines, derived attributes will have an oval with dashed lines.

## Conclusion

In this demo, we analyzed business requirements for SD-Med and created an entity-relationship diagram (ERD) to serve as the conceptual data model.
