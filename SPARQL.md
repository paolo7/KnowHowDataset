## Statistics

The results of these queries were computed over the whole [dataset](https://datahub.io/dataset/human-activities-and-instructions), loaded on Virtuoso 07.20.3215.

 Query Number | Statistic | Value 
----|----|-----
1 | Number of triples | 23,033,490 | 
2 | Number labelled nodes | 2,610,223 |
3 | Number of main processes | 215,959 |

## Query Prefixes

Standard prefixes for all the queries:
```
PREFIX prohow: <http://w3id.org/prohow#> 
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> 
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#> 
PREFIX oa: <http://www.w3.org/ns/oa#> 
```

## Queries

Query 1) Count the number of triples:
```
SELECT (COUNT(*) AS ?no) WHERE { ?s ?p ?o  }
```
Query 2) Count the number of entities with an associated label:
```
SELECT (COUNT(distinct ?s) AS ?no) WHERE { ?s rdfs:label ?o  }
```
Query 3) Count of number of distinct sets of instructions
```
SELECT (COUNT(distinct ?main) AS ?no) WHERE { ?main rdf:type prohow:instruction_set }
 ```
 Query 4) Search main sets of instructions that contain substring "create an email account" in the label:
 ```
SELECT ?main ?label WHERE { 
  ?main rdf:type prohow:instruction_set .
  ?main rdfs:label ?label 
  FILTER regex(str(?label), "create an email account", "i" )
} LIMIT 100
```
Query 5) Select the various methods of a process (query result is empty if the process does not have sub-methods):
 ```
SELECT ?method ?label WHERE { 
  <http://vocab.inf.ed.ac.uk/procont#?url=http://www.wikihow.com/create-an-email-account&t=1396532526446&n=1068622&k=mainentity> prohow:has_method ?method . 
  ?method rdfs:label ?label 
} LIMIT 100
```
Query 6) Select the various steps of a process (query result is empty if the process does not have sub-steps):
```
SELECT ?step ?label WHERE { 
  <http://vocab.inf.ed.ac.uk/procont#?url=http://www.wikihow.com/create-an-email-account&t=1396532526447&n=1068628> prohow:has_step ?step . 
  ?step rdfs:label ?label 
} LIMIT 100
 ```
 Query 7) Select the various requirements of a process (query result is empty if the process does not have requirements):
  ```
SELECT ?requirement ?label WHERE { 
  <http://vocab.inf.ed.ac.uk/procont#?url=http://www.wikihow.com/make-pizza-dough&t=1396510456016&n=11094&k=mainentity> prohow:requires ?requirement . 
  ?requirement rdfs:label ?label 
} LIMIT 100
 ```
 Query 8) Like Query 7), but optionally return the DBpedia resource linked to each requirement (when available):
  ```
SELECT ?requirement ?label ?type WHERE { 
  <http://vocab.inf.ed.ac.uk/procont#?url=http://www.wikihow.com/make-pizza-dough&t=1396510456016&n=11094&k=mainentity> prohow:requires ?requirement . 
  ?requirement rdfs:label ?label 
  OPTIONAL {?requirement rdf:type ?type} 
} LIMIT 100
 ```
 Query 9) Find the 100 most common requirements
  ```
SELECT ?type (COUNT (DISTINCT ?main) as ?no) WHERE { 
  ?main prohow:requires ?requirement .
  ?requirement rdf:type ?type
} GROUP BY ?type ?no ORDER BY desc(?no) LIMIT 100
 ```
  Query 10) Find the 100 most common outputs
  ```
SELECT ?type (COUNT (DISTINCT ?output) as ?no) WHERE { 
  ?main rdf:type prohow:instruction_set .
  ?output prohow:has_method ?main .
  ?output rdf:type ?type
} GROUP BY ?type ?no ORDER BY desc(?no) LIMIT 100
 ```
 Query 11) Find the type of requirements most correlated with a particular requirement (in this example, what is usually used in conjunction with *Paper*?):
  ```
SELECT ?type (COUNT (DISTINCT ?other_req) as ?no)
WHERE { 
  ?main rdf:type prohow:instruction_set .
  ?main prohow:requires ?requirement . 
  ?requirement rdf:type <http://dbpedia.org/resource/Paper> .
  ?main prohow:requires ?other_req . 
  ?other_req rdf:type ?type
} GROUP BY ?type ORDER BY desc(?no) LIMIT 100
 ```
