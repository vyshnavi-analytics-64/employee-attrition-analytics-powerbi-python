## Headcount & Employee Status

### Total Employees
```DAX
Total Employees =
DISTINCTCOUNT ( Employee[EmployeeID] )
Active Employees =
CALCULATE (
    DISTINCTCOUNT ( Employee[EmployeeID] ),
    Employee[Employee Status] = "Active"
)
Exited Employees =
CALCULATE (
    DISTINCTCOUNT ( Employee[EmployeeID] ),
    Employee[Employee Status] = "Exited"
)



## SECTION 2 — Attrition Metrics


## Attrition Metrics

### Attrition Rate %
```DAX
Attrition Rate % =
DIVIDE (
    [Exited Employees],
    [Total Employees],
    0
)
Attrition Rate Last Month =
CALCULATE (
    [Attrition Rate %],
    DATEADD ( 'Date Table'[Date], -1, MONTH )
)
Total Exit =
COUNTROWS (
    FILTER (
        Employee_Detail,
        NOT ISBLANK ( Employee_Detail[exit_date] )
    )
)
Female Attrition % =
CALCULATE (
    [Attrition Rate %],
    Employee_Detail[gender] = "Female"
)

This shows:
- Time intelligence
- Filter context control
- Business segmentation

---

## SECTION 3 — Age & Tenure Logic

## Age & Tenure Classification

### Age Group
```DAX
Age Group =
SWITCH (
    TRUE (),
    Employee_Detail[age] < 25, "Under 25",
    Employee_Detail[age] <= 34, "25-34",
    Employee_Detail[age] <= 44, "35-44",
    Employee_Detail[age] <= 54, "45-54",
    "55+"
)
Tenure Years =
VAR EndDate =
    IF (
        ISBLANK ( Employee_Detail[exit_date] ),
        TODAY (),
        Employee_Detail[exit_date]
    )
RETURN
    DATEDIFF ( Employee_Detail[hire_date], EndDate, YEAR )
Tenure Band =
SWITCH (
    TRUE (),
    [Tenure Years] <= 2, "0-2 Years",
    [Tenure Years] <= 5, "3-5 Years",
    [Tenure Years] <= 10, "6-10 Years",
    "10+ Years"
)


## SECTION 4 — Performance & Experience


## Performance Metrics

### Average Experience
```DAX
Average Experience =
AVERAGE ( Employee_Detail[experience_(years)] )
Average Performance =
AVERAGE ( Employee_Detail[performance_rating] )

---

## SECTION 5 — Sorting Logic (VERY IMPORTANT)


## Sorting Columns

### Salary Band Sort
```DAX
Salary Band Sort =
SWITCH (
    Employee_Detail[salary_band],
    "< $50k", 1,
    "$50k-75k", 2,
    "$75k-110k", 3,
    "> $110k", 4,
    5
)
Tenure Sort =
SWITCH (
    Employee_Detail[Tenure Band],
    "0-2 Years", 1,
    "3-5 Years", 2,
    "6-10 Years", 3,
    "10+ Years", 4
)
