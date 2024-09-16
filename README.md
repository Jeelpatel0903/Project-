[link]="https://www.canva.com/design/DAF8x1L4B2M/F8lo6BpNfLO_pLQe_kFayg/view?utm_content=DAF8x1L4B2M&utm_campaign=designshare&utm_medium=link&utm_source=publishsharelink&mode=preview"


[link]="https://www.canva.com/design/DAF88jaTY0g/zaX_lgU_cZa6AkGzHsAekg/view?utm_content=DAF88jaTY0g&utm_campaign=designshare&utm_medium=link&utm_source=editor"

[link]="https://www.canva.com/design/DAF88jaTY0g/0KqpgEtXox36maoaBCa-Iw/view?utm_content=DAF88jaTY0g&utm_campaign=designshare&utm_medium=link&utm_source=publishsharelink&mode=preview"




https://www.canva.com/design/DAF8x1L4B2M/k7hnoWwX4xfQS8naMCaFfg/view?utm_content=DAF8x1L4B2M&utm_campaign=designshare&utm_medium=link&utm_source=editor



[link]="https://chat.openai.com/c/a5657e16-b8bb-4e8b-8cc9-8ccdea1c10f1"














Here’s the updated version based on your request:

---

**Suggestion for Improvement:**

In the current system, there is a popup displaying all employees in a grid with options to select or multi-select employees and assign them.

I suggest adding a switch toggle at the top of the popup with two values: "Assigned" and "Unassigned." When the toggle is set to "Assigned," it will display employees who are already assigned to other agencies. When the toggle is set to "Unassigned," it will display employees who are not assigned to any other agency.

This change will simplify the process of managing employees, as users can focus on one action at a time. For instance, when the toggle is on "Assigned," users can view and manage employees already assigned to other agencies. When it’s on "Unassigned," users can assign employees who are not yet assigned to any agency.

---

This should now align with the functionality you're describing.









Employee Table:
| Column Name  | Data Type    | Description                             |
|--------------|--------------|-----------------------------------------|
| id           | INT          | Primary key                             |
| Name         | NVARCHAR(255)| Employee name                           |



AdditionDeduction Table:

| Column Name     | Data Type    | Description                             |
|-----------------|--------------|-----------------------------------------|
| id              | INT          | Primary key                             |
| Name            | NVARCHAR(255)| Name of addition/deduction              |
| Type            | CHAR(1)      | Type of addition/deduction              |
| DefaultAmount   | DOUBLE       | Default amount for addition/deduction   |
| CreatedBy       | INT          | ID of the user who created the record   |
| UpdatedBy       | INT          | ID of the user who last updated the record|
| CreatedOn       | DATETIME     | Timestamp of creation                   |
| UpdatedOn       | DATETIME     | Timestamp of last update                |
| DeletedBy       | INT          | ID of the user who deleted the record   |

EmployeeSalaryConfiguration Table:
| Column Name          | Data Type    | Description                             |
|----------------------|--------------|-----------------------------------------|
| id                   | INT          | Primary key                             |
| EmployeeID           | INT          | Foreign key referencing Employee table  |
| AdditionDeductionId  | INT          | Foreign key referencing AdditionDeduction table|
| Amount               | DOUBLE       | Amount for the configuration            |
| EffectiveDate        | DATETIME     | Effective date of the configuration     |
| EndDate              | DATETIME     | End date of the configuration           |
| CreatedBy            | INT          | ID of the user who created the record   |
| UpdatedBy            | INT          | ID of the user who last updated the record|
| CreatedOn            | DATETIME     | Timestamp of creation                   |
| UpdatedOn            | DATETIME     | Timestamp of last update                |
| DeletedBy            | INT          | ID of the user who deleted the record   |


EmployeeSalarySummary Table:
| Column Name     | Data Type    | Description                             |
|-----------------|--------------|-----------------------------------------|
| id              | INT          | Primary key                             |
| EmployeeID      | INT          | Foreign key referencing Employee table  |
| Period          | INT          | Period identifier                       |
| FinancialYear   | DATETIME     | Financial year of the summary           |
| TotalAddition   | DOUBLE       | Total amount of all additions for the period |
| TotalDeduction  | DOUBLE       | Total amount of all deductions for the period |
| NetSalary       | DOUBLE       | Net salary after subtracting deductions from additions |
| CreatedBy       | INT          | ID of the user who created the record   |
| UpdatedBy       | INT          | ID of the user who last updated the record|
| CreatedOn       | DATETIME     | Timestamp of creation                   |
| UpdatedOn       | DATETIME     | Timestamp of last update                |
| DeletedBy       | INT          | ID of the user who deleted the record   |


Timesheet Table:
| Column Name                 | Data Type    | Description                             |
|-----------------------------|--------------|-----------------------------------------|
| id                          | INT          | Primary key                             |
| EmployeeID                  | INT          | Foreign key referencing Employee table  |
| CompanyID                   | INT          | Foreign key referencing Company table   |
| EmployeeSalaryConfigurationId| INT         | Foreign key referencing EmployeeSalaryConfiguration table|
| EmployeeSalarySummaryId     | INT          | Foreign key referencing EmployeeSalarySummary table|
| Status                      | NVARCHAR(255)| Status of the timesheet                 |
| HoursWorked                 | INT          | Hours worked by the employee            |
| LeaveTaken                  | INT          | Leave taken by the employee             |
| OvertimeHours               | INT          | Overtime hours worked by the employee   |
| CreatedBy                   | INT          | ID of the user who created the record   |
| UpdatedBy                   | INT          | ID of the user who last updated the record|
| CreatedOn                   | DATETIME     | Timestamp of creation                   |
| UpdatedOn                   | DATETIME     | Timestamp of last update                |
| DeletedBy                   | INT          | ID of the user who deleted the record   |

YtdSummary Table:
| Column Name            | Data Type    | Description                             |
|------------------------|--------------|-----------------------------------------|
| id                     | INT          | Primary key                             |
| EmployeeSalarySummaryId| INT          | Foreign key referencing EmployeeSalarySummary table|
| AdditionDeductionId    | INT          | Foreign key referencing AdditionDeduction table|
| YtdAmount              | DOUBLE       | Year-to-date amount                     |



Company Table:
| Column Name  | Data Type    | Description                             |
|--------------|--------------|-----------------------------------------|
| id           | INT          | Primary key                             |
| Name         | NVARCHAR(255)| Company name                            |
| Address      | NVARCHAR(255)| Company address                         |
| Logo         | NVARCHAR(255)| URL of the company logo                 |



