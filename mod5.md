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

### Sintaxi de atorgació de privilegis
```sql
GRANT <privilegis> TO <autoritzat> [{ , <autoritzat>}]
	[WITH HIERARCHY OPTION]
	[WITH GRANT OPTION]
	[GRANTED BY <autoritzador>]
<privilegis> ::=
	<privilegis d'objecte> ON <nom objecte>
<privilegis d'objecte> ::=
	ALL PRIVILEGES|<acció>[{ , <acció>}]
<acció> ::=
	DELETE |
	SELECT [(<nom columna> [ , <nom columna>] ... ])]|
	SELECT [(<nom rut ina> [ , <nom rutina>] ... ])]|
	INSERT [(<nom columna> [ , <nom columna>] ... ])]|
	UPDATE [(<nom columna> [ , <nom columna>] ... ])]|
	REFERENCES [(<nom columna> [ , <nom columna> ... ])]|
	USAGE |
	UNDER |
	TRIGGER |
	EXECUTE


<nom objecte> ::=
	[ TABLE ] <nom taula>
	|DOMAIN <nom domini>
	| COLLATION <nom compaginador de caràcters>
	| CHARACTER SET <nom joc de caràcters>
	| TRANSLATION <nom transcripció>
	| TYPE <nom tipus>
	| SEQUENCE <nom generador de seqüències>
	| <designador específic de rutina>
	| MODULE <nom mòdul>

<autoritzat> ::=
	PUBLIC | <nom autoritzat>
<autoritzador> ::=
	CURRENT_USER | CURRENT_ROLE
```

Creació de rol:
```sql
<definició rol> ::=
	CREATE ROLE <nom rol>
	[WITH ADMIN <autoritzador>]
<sentència autorització rol> ::=
	GRANT <nom rol> [ { , <nom rol>}]
	TO <autoritzat> [ { , <autoritzat>}]
	[WITH GRANT OPTION]
	[GRANTED BY <autoritzador>]
```
