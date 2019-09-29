# Neo4j/Cypher - Exemplo

```
CREATE (n)
```

```
CREATE (n),(m)

```

```
CREATE (n:Person)
```

```
CREATE (n:Person:Professor),(u:Person:Student)
```

```
CREATE (n:Person:Student { name: 'Asdrubal', cpf: '1111155554' })
```

```
CREATE (n:Person:Professor { name: 'Doriana', cpf: '888888777778' })
RETURN n.name
```


```
MATCH (a:Person),(b:Person)
WHERE a.name = 'Asdrubal' AND b.name = 'Doriana'
CREATE (a)-[r:WAS_ADVISED_BY]->(b)
RETURN type(r)
```


```
MATCH (a:Person)-[r]-(b:Person)
WHERE a.name = 'Asdrubal' AND b.name = 'Doriana'
RETURN r
```


```
MATCH (a:Person)-[r]-(b:Person)
WHERE a.name = 'Asdrubal' AND b.name = 'Doriana'
SET r.type = 'tcc',
    r.year = 1982 
RETURN r
```


```sql
LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/matheusmota/facens-dataviz/master/resources/datasets/movies.csv' AS line
MERGE (m:Movie { title: line.title })
ON CREATE SET m.released = toInteger(line.released), m.tagline = line.tagline
```

```sql
LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/matheusmota/facens-dataviz/master/resources/datasets/actors.csv' AS line
MATCH (m:Movie { title: line.title })
MERGE (p:Person { name: line.name })
ON CREATE SET p.born = toInteger(line.born)
MERGE (p)-[:ACTED_IN { roles:split(line.roles, ';')}]->(m)
```


```sql
LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/matheusmota/facens-dataviz/master/resources/datasets/directors.csv' AS line
MATCH (m:Movie { title: line.title })
MERGE (p:Person { name: line.name })
ON CREATE SET p.born = toInteger(line.born)
MERGE (p)-[:DIRECTED]->(m)
```

```
MATCH (p { name: 'Tom Hanks' })
RETURN p
```

```
MATCH (p:Person { name: 'Tom Hanks' })
RETURN p
```



