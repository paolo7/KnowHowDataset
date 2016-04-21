## Statistics

The results of these queries were computed over the whole dataset, loaded on Virtuoso 07.20.3215.

 Query Number | Statistic | Value 
----|----|-----
1 | Number of triples | 23,033,490 | 
2 | Number labelled nodes | 2,610,223 |
3 | Number of main processes | 215,959 |

## Queries

Standard prefix for all the queries:
```
PREFIX prohow: <http://w3id.org/prohow#> 
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> 
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#> 
PREFIX oa: <http://www.w3.org/ns/oa#> 
```
Query 1) Count the number of triples:
```
SELECT (COUNT(*) AS ?no) where { ?s ?p ?o  }
```
Query 2) Count the number of entities with an associated label:
```
SELECT (COUNT(distinct ?s) AS ?no) where { ?s rdfs:label ?o  }
```
Query 3) Count of number of distinct sets of instructions
```
SELECT (COUNT(distinct ?main) AS ?no) where { ?main rdf:type prohow:instruction_set }
 ```
 Query 4) Search main sets of instructions that contain substring "create an email account" in the label:
 ```
SELECT ?main ?label where { 
  ?main rdf:type prohow:instruction_set .
  ?main rdfs:label ?label 
  FILTER regex(str(?label), "create an email account", "i" )
} LIMIT 100
```
Query 5) Select the various methods of a set of instructions (query result is empty if the set of instructions does not have sub-methods)
 ```
SELECT ?method ?label where { 
  <http://vocab.inf.ed.ac.uk/procont#?url=http://www.wikihow.com/create-an-email-account&t=1396532526446&n=1068622&k=mainentity> prohow:has_method ?method . 
  ?method rdfs:label ?label 
} LIMIT 100
```
Query 6) Select the various steps of a set of instructions (query result is empty if the set of instructions does not have sub-steps)
```
SELECT ?step ?label where { 
  <http://vocab.inf.ed.ac.uk/procont#?url=http://www.wikihow.com/create-an-email-account&t=1396532526447&n=1068628> prohow:has_step ?step . 
  ?step rdfs:label ?label 
} LIMIT 100
 ```
