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

Query 1)
```
SELECT (COUNT(*) AS ?no) where { ?s ?p ?o  }
```
Query 2)
```
SELECT (COUNT(distinct ?s) AS ?no) where { ?s rdfs:label ?o  }
```
Query 3)
```
SELECT (COUNT(distinct ?main) AS ?no) where { ?main rdf:type prohow:instruction_set }
 ```
