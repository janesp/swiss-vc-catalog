#Employee
Generated using [DbSchema](https://dbschema.com)




### Employee
![img](./Employee.svg)



### Entity INSTANCE.Authorisation 
| | | | |
|---|---|---|---|
| * &#11016; | ID| BIGINT  |  |
| * | Issue Date| DATE  |  |
| * | Employee ID| INT  | Redundant onformation of «Employee Core».\&gt;&gt; Review - remove |
| * &#128273;  | Authorisation ID| INT  |  |
| * | Authorisation Type| VARCHAR(100)  | &gt;&gt; Review - valid value set? Alternatively use predefined code instead of free text. |


##### Indexes 
| | | |
|---|---|---|
| &#128273;  | pk\_Authorisation | ON Authorisation ID|

##### Relationships
| | | |
|---|---|---|
|  | Authorisation - Employee Core | ( ID ) ref [INSTANCE.Employee Core](#Employee Core) (ID) |




### Entity INSTANCE.Employee Core 
Common core information for employee.

| | | | |
|---|---|---|---|
| * &#128273;  &#11019; | ID| BIGINT  | Technical ID assigned through VC issuing process. |
| * | Issue Date| DATE  | Issue of VC. |
| * | Employee ID| BIGINT  | ID assigned by employer. |
| * | Name| VARCHAR(100)  | Aliases - last name, family name |
| * | Given Name| VARCHAR(100)  | Alias - first name |
|  | Birth Date| DATE  | Alias - date of birth (DOB) |
| * | Employer| VARCHAR(100)  | Employer name (note - alternatively, an employer number could be used). |
| * | Employment Date| DATE  | Based on contract. |
|  | Leave Date| DATE  |  |


##### Indexes 
| | | |
|---|---|---|
| &#128273;  | pk\_Employee Core | ON ID|



### Entity INSTANCE.Employee Extended 
| | | | |
|---|---|---|---|
| * &#128273;  &#11016; | ID| BIGINT  |  |
| * | Issue Date| DATE  |  |
| * | Employee ID| BIGINT  | Redundant onformation of «Employee Core».\&gt;&gt; Review - remove |
| * | Employer| BIGINT  | Redundant onformation of «Employee Core».\&gt;&gt; Review - remove |
|  | Operation Site| VARCHAR(100)  | Free text - address or similar. |
|  | Activity Tyoe| VARCHAR(100)  | Free text.\&gt;&gt; Review - optionally based on list of values |
|  | Contact Name| VARCHAR(100)  | First name, last name\&gt;&gt; Review - reference to person |
|  | Contact Phone| VARCHAR(100)  | &gt;&gt; Review - reference to person |
|  | Contact Mail| VARCHAR(100)  | &gt;&gt; Review - reference to person |


##### Indexes 
| | | |
|---|---|---|
| &#128273;  | pk\_Employee Extended | ON ID|

##### Relationships
| | | |
|---|---|---|
|  | Employee Extended - Employee Core | ( ID ) ref [INSTANCE.Employee Core](#Employee Core) (ID) |




### Entity INSTANCE.Employee Role 
| | | | |
|---|---|---|---|
| * &#128273;  &#11016; | ID| BIGINT  |  |
| * | Issue Date| DATE  |  |
| * | Employee ID| BIGINT  | Redundant onformation of «Employee Core».\&gt;&gt; Review - remove |
|  | Role| VARCHAR(100)  | &gt;&gt; Review - valid value set? Alternatively use predefined code instead of free text. |
|  | Function| VARCHAR(100)  | &gt;&gt; Review - valid value set? Alternatively use predefined code instead of free text. |
|  | Organisational Unit| VARCHAR(100)  | &gt;&gt; Review - valid value set? Alternatively use predefined code instead of free text. |


##### Indexes 
| | | |
|---|---|---|
| &#128273;  | pk\_Employee Role | ON ID|

##### Relationships
| | | |
|---|---|---|
|  | Employee Role - Employee Core | ( ID ) ref [INSTANCE.Employee Core](#Employee Core) (ID) |




### Entity INSTANCE.Employer Address 
| | | | |
|---|---|---|---|
| * &#128273;  &#11016; | ID| BIGINT  |  |
| * | Issue Date| DATE  |  |
| * | Empoyee ID| BIGINT  | Redundant onformation of «Employee Core».\&gt;&gt; Review - remove |
|  | Street Address| VARCHAR(100)  |  |
|  | Postal Code| VARCHAR(10)  |  |
|  | City| VARCHAR(100)  |  |


##### Indexes 
| | | |
|---|---|---|
| &#128273;  | pk\_Employer Address | ON ID|

##### Relationships
| | | |
|---|---|---|
|  | Employer Address - Employee Core | ( ID ) ref [INSTANCE.Employee Core](#Employee Core) (ID) |




### Entity INSTANCE.Employment 
Employment information of a person (employee).

| | | | |
|---|---|---|---|
| * &#128273;  &#11016; | ID| BIGINT  |  |
| * | Issue Date| DATE  |  |
| * | Employee ID| BIGINT  | Redundant onformation of «Employee Core».\&gt;&gt; Review - remove |
| * | Contract Type| ENUM(up to  364 days, 365 days and more)  |  |
| * | Weekly Work Hours| INT  | According to contract. |
| * | Salary| BIGINT  | Annual base salary, CHF. |
|  | Entry Date| DATE  | First working day. |


##### Indexes 
| | | |
|---|---|---|
| &#128273;  | pk\_Employment | ON ID|

##### Relationships
| | | |
|---|---|---|
|  | Employment - Employee Core | ( ID ) ref [INSTANCE.Employee Core](#Employee Core) (ID) |





