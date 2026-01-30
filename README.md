## Employee DB ERD

```mermaid
erDiagram
    DEPARTMENT {
        CHAR(2) DEPT_ID PK
        VARCHAR DEPT_TITLE
        CHAR(2) LOCATION_ID FK
    }

    EMPLOYEE {
        VARCHAR(3) EMP_ID PK
        VARCHAR EMP_NAME
        CHAR(14) EMP_NO
        VARCHAR EMAIL
        VARCHAR PHONE
        CHAR(2) DEPT_CODE FK
        CHAR(2) JOB_CODE FK
        CHAR(2) SAL_LEVEL FK
        DECIMAL SALARY
        DECIMAL BONUS
        VARCHAR(3) MANAGER_ID FK
        DATE HIRE_DATE
        DATE ENT_DATE
        CHAR(1) ENT_YN
    }

    JOB {
        CHAR(2) JOB_CODE PK
        VARCHAR JOB_NAME
    }

    LOCATION {
        CHAR(2) LOCAL_CODE PK
        CHAR(2) NATIONAL_CODE FK
        VARCHAR LOCAL_NAME
    }

    NATIONAL {
        CHAR(2) NATIONAL_CODE PK
        VARCHAR NATIONAL_NAME
    }

    SAL_GRADE {
        CHAR(2) SAL_LEVEL PK
        DECIMAL MIN_SAL
        DECIMAL MAX_SAL
    }

    DEPARTMENT ||--o{ EMPLOYEE : has
    JOB ||--o{ EMPLOYEE : assigned_to
    SAL_GRADE ||--o{ EMPLOYEE : salary_level
    LOCATION ||--o{ DEPARTMENT : located_in
    NATIONAL ||--o{ LOCATION : belongs_to
    EMPLOYEE ||--o{ EMPLOYEE : manages
