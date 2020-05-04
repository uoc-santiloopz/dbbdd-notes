# Disseny físic de bbdd

## Creació d'índex en Oracle

### Accessos per valor
Asc: `CREATE INDEX <indexName> ON <Table> (<attr>);`  
Desc: `CREATE INDEX <indexName> ON <Table> (<attr> DESC);`

Per aconseguir que l'índex sigui agrupat:  
`CREATE CLUSTER INDEX <indexName> ON <Table> (<attr>);`  

Si volem que no admeti valors repetits:  
`CREATE UNIQUE INDEX <indexName> ON <Table> (<attr>);`


### Accessos per diversos valors
Asc: `CREATE INDEX <indexName> ON <Table> (<attr1>, <attr2>..., <attrN>);`  


## Exemple de clau sintética sequencial
```sql
CREATE TABLE Worker (
	idWorker INTEGER CONSTRAINT PK_Worker PRIMARY KEY,
	nif VARCHAR2(10 CHAR) CONSTRAINT AK_Worker UNIQUE,
	name VARCHAR2(100 CHAR) CONSTRAINT NN_WorkerName NOT NULL,
	specialty VARCHAR2(11 CHAR) CONSTRAINT NN_WorkerSpecialty NOT NULL
	CONSTRAINT CH_WorkerSpecialty CHECK (specialty = 'ENGINEERING' OR
										specialty = 'SUPPORT' OR
										specialty = 'DEVELOPMENT'),
	years INTEGER CONSTRAINT NN_WorkerYears NOT NULL
	CONSTRAINT CH_WorkerYears CHECK (years >= 1)
);

-- Creació de seqüencia per a obtenir el valor en curs del treballador a inserir
CREATE SEQUENCE s_Worker
	INCREMENT BY 1
	START WITH 1;

-- Creació del disparador que inserirà automàticament el valor a idWorker
CREATE OR REPLACE TRIGGER t_sintetic_idWorker
	BEFORE INSERT ON Worker
	FOR EACH ROW

BEGIN
	SELECT s_Worker.NEXTVAL INTO :NEW.idWorker FROM DUAL;

END t_sintetic_idWorker;
```