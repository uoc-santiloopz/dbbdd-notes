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