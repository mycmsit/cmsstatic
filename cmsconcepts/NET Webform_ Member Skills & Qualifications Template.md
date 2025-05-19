# .NET Webform: Member Skills & Qualifications Template
Created: 2025/05/07, 21:21:05
Last Updated: 2025/05/07, 21:21:15
---

### User

I have a aspx .net 4.8.1 webform with c# and Bootstrap 5 

I have a members_all table and the members has an occupation, skill and qualifications. I need a template per memberID to control these

I suggest a MememberCapabilities tables with there memberid, ,the type of skill and a ranking of 1-10 per skill, also paid for skill or non paid. And a column for their offer to the church for probona.

We need to have categories for 0ccupation/Skills/Qualifications/Level of qualification (like Matric/diploma/degree)

Then unemployed as a cat.

each must be ranked.


---

### Assistant (gpt-4.1)

Absolutely, Lee-Anne! Your requirements are clear and practical for a church or community database. Here’s a **summary and a suggested schema** for your scenario, using best practices for normalisation and future-proofing.

---

## **Summary of Requirements**

- **Members** have:  
  - Occupation(s)
  - Skill(s)
  - Qualification(s)
  - Each with a ranking (1–10)
  - Paid or non-paid skill
  - Pro bono offer to the church
  - Level of qualification (e.g., Matric, Diploma, Degree)
  - Unemployed as a category

---

## **Suggested Database Schema**

### **1. Members Table**
Stores basic member info.

| Column Name   | Type         | Description                |
|---------------|--------------|----------------------------|
| MemberID      | int (PK)     | Unique member identifier   |
| Name          | nvarchar     | Member's name              |
| ...           | ...          | Other member details       |

---

### **2. Capabilities Table**
Stores all capabilities (occupation, skill, qualification) per member.

| Column Name         | Type         | Description                                 |
|---------------------|--------------|---------------------------------------------|
| CapabilityID        | int (PK)     | Unique capability record                    |
| MemberID            | int (FK)     | Linked to Members table                     |
| CapabilityType      | varchar      | 'Occupation', 'Skill', 'Qualification'      |
| CapabilityName      | nvarchar     | Name of the skill/occupation/qualification  |
| Level               | varchar      | e.g., 'Matric', 'Diploma', 'Degree'         |
| Ranking             | int          | 1–10                                        |
| Paid                | bit          | 1 = paid, 0 = non-paid                      |
| ProBonoOffer        | bit          | 1 = offers pro bono, 0 = does not           |
| DateAdded           | datetime     | For auditing                                |

---

### **3. Unemployment Table (Optional)**
If you want to track unemployment as a separate category.

| Column Name   | Type         | Description                |
|---------------|--------------|----------------------------|
| MemberID      | int (FK)     | Linked to Members table    |
| IsUnemployed  | bit          | 1 = unemployed, 0 = not    |
| DateUpdated   | datetime     | Last status update         |

---

## **How it Works**

- **Each member** can have multiple entries in the Capabilities table, one per skill/occupation/qualification.
- **Ranking** allows you to sort or filter by proficiency or importance.
- **Paid/Pro bono** flags help you identify which skills are offered for free to the church.
- **Level** is only relevant for qualifications, but you can leave it null for skills/occupations.
- **Unemployed** can be a capability or a separate flag.

---

## **Example Data**

| MemberID | CapabilityType | CapabilityName | Level   | Ranking | Paid | ProBonoOffer |
|----------|---------------|---------------|---------|---------|------|--------------|
| 1        | Occupation    | Electrician   |         | 8       | 1    | 1            |
| 1        | Skill         | Carpentry     |         | 6       | 0    | 1            |
| 1        | Qualification | Diploma       | Diploma | 7       |      |              |
| 2        | Occupation    | Unemployed    |         |         |      |              |

---

## **ASPX Template Suggestion**

You can use a **Repeater** or **GridView** to display and edit capabilities per member.  
Each row can have dropdowns for type, name, level, ranking, and checkboxes for paid/pro bono.

---

## **Next Steps**

- **Create the tables** in SQL Server.
- **Build a webform** to add/edit capabilities per member.
- **Use Bootstrap 5** for responsive forms and tables.

---

**Let me know if you want:**
- Example SQL table creation scripts
- Example ASPX markup and C# code-behind
- Advice on the UI/UX for the webform

Happy to help you get started!


---
