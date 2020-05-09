# Processament de consultes i vistes

### Sintaxi de la creació de vistes:
```sql
CREATE VIEW ViewName [(column_name), ... ]
AS query
[WITH [CASCADED|LOCAL]CHECK OPTION ]
```

Altre exemple:
```sql
CREATE VIEW View01 AS
	SELECT firstName, lastName, hireDate, salary
	FROM Emp e
	WHERE salary < 30000;
CREATE VIEW View02 AS
	SELECT firstName, lastName, deptName
	FROM Emp e, Dept d
	WHERE e.deptId = d.deptId;
CREATE VIEW View03 AS
	SELECT *
	FROM View02
	WHERE (firstName, lastName) IN (SELECT firstName, lastName FROM View01);
```