<!--
 ___ _            _ _    _ _    __
/ __(_)_ __  _ __| (_)__(_) |_ /_/
\__ \ | '  \| '_ \ | / _| |  _/ -_)
|___/_|_|_|_| .__/_|_\__|_|\__\___|
            |_| 
-->
![](https://docs.simplicite.io//logos/logo250.png)
* * *

`Projects` module definition
============================

Software project management

`PrjItem` business object definition
------------------------------------

Work Item

### Fields

| Name                                                         | Type                                     | Required | Updatable | Personal | Description                                                                      | 
| ------------------------------------------------------------ | ---------------------------------------- | -------- | --------- | -------- | -------------------------------------------------------------------------------- |
| `prjItmVrsId` link to **`PrjVersion`**                       | id                                       | yes      | yes       |          | -                                                                                |
| _Ref. `prjItmVrsId.prjVrsPrjId`_                             | _id_                                     |          |           |          | -                                                                                |
| _Ref. `prjVrsPrjId.prjPrjName`_                              | _char(100)_                              |          |           |          | -                                                                                |
| _Ref. `prjItmVrsId.prjVrsVersion`_                           | _char(10)_                               |          |           |          | -                                                                                |
| _Ref. `prjItmVrsId.prjVrsDueDate`_                           | _date_                                   |          |           |          | -                                                                                |
| `prjItmUsrId` link to **`PrjUser`**                          | id                                       | yes      | yes       |          | -                                                                                |
| _Ref. `prjItmUsrId.usr_login`_                               | _regexp(100)_                            |          |           | yes      | _Login_                                                                          |
| `prjItmStatus`                                               | enum(7) using `PRJITMSTATUS` list        | yes      | yes       |          | -                                                                                |
| `prjItmPriority`                                             | enum(7) using `PRJITMPRIORITY` list      | yes      | yes       |          | -                                                                                |
| `prjItmCreated`                                              | datetime                                 |          |           |          | -                                                                                |
| `prjItmProgress`                                             | float(3, 0)                              |          | yes       |          | -                                                                                |
| `prjItmDescription`                                          | text(10000)                              |          | yes       |          | -                                                                                |
| `prjItmNumber`                                               | int(11)                                  | yes*     |           |          | -                                                                                |
| `prjItmTitle`                                                | char(255)                                | yes      | yes       |          | -                                                                                |
| `prjItmPrjId` link to **`PrjProject`**                       | id                                       |          | yes       |          | -                                                                                |

### Lists

* `PRJITMSTATUS`
    - `DRAFT` Draft
    - `BACKLOG` Backlog
    - `SPRINT` Sprint
    - `DOING` Doing
    - `DONE` Done
    - `CLOSED` Closed
    - `REJECTED` Rejected
* `PRJITMPRIORITY`
    - `LOW` Low
    - `NORMAL` Normal
    - `HIGH` High
    - `URGENT` Urgent

`PrjItmAttachements` business object definition
-----------------------------------------------



### Fields

| Name                                                         | Type                                     | Required | Updatable | Personal | Description                                                                      | 
| ------------------------------------------------------------ | ---------------------------------------- | -------- | --------- | -------- | -------------------------------------------------------------------------------- |
| `prjItattItmId` link to **`PrjItem`**                        | id                                       | yes      | yes       |          | -                                                                                |
| _Ref. `prjItattItmId.prjItmNumber`_                          | _int(11)_                                |          |           |          | -                                                                                |
| `prjItattFile`                                               | document                                 | yes*     | yes       |          | -                                                                                |

`PrjLabel` business object definition
-------------------------------------



### Fields

| Name                                                         | Type                                     | Required | Updatable | Personal | Description                                                                      | 
| ------------------------------------------------------------ | ---------------------------------------- | -------- | --------- | -------- | -------------------------------------------------------------------------------- |
| `prjLblName`                                                 | char(30)                                 | yes*     | yes       |          | -                                                                                |

`PrjLblItm` business object definition
--------------------------------------



### Fields

| Name                                                         | Type                                     | Required | Updatable | Personal | Description                                                                      | 
| ------------------------------------------------------------ | ---------------------------------------- | -------- | --------- | -------- | -------------------------------------------------------------------------------- |
| `prjLblitmLblId` link to **`PrjLabel`**                      | id                                       | yes*     | yes       |          | -                                                                                |
| _Ref. `prjLblitmLblId.prjLblName`_                           | _char(30)_                               |          |           |          | -                                                                                |
| `prjLblitmItmId` link to **`PrjItem`**                       | id                                       | yes*     | yes       |          | -                                                                                |

`PrjProject` business object definition
---------------------------------------



### Fields

| Name                                                         | Type                                     | Required | Updatable | Personal | Description                                                                      | 
| ------------------------------------------------------------ | ---------------------------------------- | -------- | --------- | -------- | -------------------------------------------------------------------------------- |
| `prjPrjName`                                                 | char(100)                                | yes*     | yes       |          | -                                                                                |
| `prjPrjDescription`                                          | text(5000)                               |          | yes       |          | -                                                                                |

`PrjRole` business object definition
------------------------------------

Role on project

### Fields

| Name                                                         | Type                                     | Required | Updatable | Personal | Description                                                                      | 
| ------------------------------------------------------------ | ---------------------------------------- | -------- | --------- | -------- | -------------------------------------------------------------------------------- |
| `prjRolPrjId` link to **`PrjProject`**                       | id                                       | yes*     | yes       |          | -                                                                                |
| _Ref. `prjRolPrjId.prjPrjName`_                              | _char(100)_                              |          |           |          | -                                                                                |
| `prjRolUsrId` link to **`PrjUser`**                          | id                                       | yes*     | yes       |          | -                                                                                |
| _Ref. `prjRolUsrId.usr_login`_                               | _regexp(100)_                            |          |           | yes      | _Login_                                                                          |
| `prjRolType`                                                 | enum(7) using `PRJROLTYPE` list          | yes*     | yes       |          | -                                                                                |

### Lists

* `PRJROLTYPE`
    - `PRJ_MOA` MOA
    - `PRJ_MOE` MOE
    - `PRJ_READONLY` Lecture seule

`PrjUser` business object definition
------------------------------------



### Fields

| Name                                                         | Type                                     | Required | Updatable | Personal | Description                                                                      | 
| ------------------------------------------------------------ | ---------------------------------------- | -------- | --------- | -------- | -------------------------------------------------------------------------------- |

`PrjVersion` business object definition
---------------------------------------



### Fields

| Name                                                         | Type                                     | Required | Updatable | Personal | Description                                                                      | 
| ------------------------------------------------------------ | ---------------------------------------- | -------- | --------- | -------- | -------------------------------------------------------------------------------- |
| `prjVrsPrjId` link to **`PrjProject`**                       | id                                       | yes      | yes       |          | -                                                                                |
| _Ref. `prjVrsPrjId.prjPrjName`_                              | _char(100)_                              |          |           |          | -                                                                                |
| `prjVrsVersion`                                              | char(10)                                 | yes*     | yes       |          | -                                                                                |
| `prjVrsDueDate`                                              | date                                     |          | yes       |          | -                                                                                |

