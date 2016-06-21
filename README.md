# The Web of Know-How: Human Activities and Instructions

## Overview

* This dataset has been produced as part of the [The Web of Know-How](http://homepages.inf.ed.ac.uk/s1054760/prohow/index.htm) project
* **To cite this dataset use:**
Paolo Pareti, Benoit Testu, Ryutaro Ichise, Ewan Klein and Adam Barker. Integrating Know-How into the Linked Data Cloud. Knowledge Engineering and Knowledge Management, volume 8876 of Lecture Notes in Computer Science, pages 385-396. Springer International Publishing (2014) 
([PDF](http://homepages.inf.ed.ac.uk/s1054760/papers/pareti_ekaw_2014.pdf)) ([bibtex](http://homepages.inf.ed.ac.uk/s1054760/bibtex/pareti2014b.bib))
* **Quickstart**: if you want to experiment with the most high-quality data before downloading all the datasets, download the file *9of11_knowhow_wikihow*, and optionally files *instruction set entities*, *Process - Inputs*, *Process - Outputs*, *Process - Step Links* and *wikiHow categories hierarchy*.
* Data representation based on the [PROHOW](http://w3id.org/prohow#) vocabulary
* Data extracted from existing web resources is linked to the original resources using the [Open Annotation](http://www.openannotation.org/spec/core/) specification
* Data also available from [datahub](https://w3id.org/knowhow/dataset)

## Available Datasets

Instruction datasets:

- Datasets *1of11_knowhow_wikihow* to *9of11_knowhow_wikihow* contain instructions from the [wikiHow](http://www.wikihow.com/) website. Instructions are allocated in the datasets in order of popularity. This means that the most popular and high-quality instructions are found in 9of11_knowhow_wikihow, while the least popular ones are in dataset 1of11_knowhow_wikihow. These instructions are also classified according to the hierarchy found in *wikiHow categories hierarchy*. wikiHow instructions are community generated. As a result of this, each task is described by at most one set of instructions, which is usually of high quality thanks to the collective community contributions.
- Datasets *10of11_knowhow_snapguide* to *11of11_knowhow_snapguide* contain instructions from the [Snapguide](https://snapguide.com/) website. These instructions are not sorted by their popularity, but they are classified in one of the Snapguide categories. Snapguide instructions are created by single users. As a result of this there might be multiple sets of instructions to achieve the same task; however these instructions on average contain more noise as they are not peer-reviewed.

Links datasets:

- The *Process - Inputs* datasets contain detailed information about the inputs of the sets of instructions, including links to [DBpedia](http://wiki.dbpedia.org/) resources
- The *Process - Outputs* datasets contains detailed information about the outputs of the sets of instructions, including links to [DBpedia](http://wiki.dbpedia.org/) resources
- The *Process - Step Links* datasets contains links between different sets of instructions

Other datasets:

- The *wikiHow categories hierarchy* dataset contains information on how the various wikiHow categories are hierarchically structured, and how they relate to the Snapguide categories.
- The *instruction set entities* dataset lists all the top-level entities in a sets of instructions. In other words, all the entities which correspond to the title of a set of instructions.
- The *wikiHow community links* dataset lists the links manually created by the wikiHow community of users that interlink entities belonging to different sets of instructions.

## Data Model

The [following figure](http://paolopareti.uk/prohow/PROHOW_DataModel_Example.pdf) is a simple example of how the [PROHOW](http://w3id.org/prohow#) vocabulary is used in the datasets. Instructions in the dataset can have more complex structures, for example instructions could have multiple methods, steps could have further sub-steps, and complex requirements could be decomposed into sub-requirements.

![example PROHOW data model](http://paolopareti.uk/prohow/PROHOW_DataModel_Example.jpg)

## SPARQL queries

Sample SPARQL queries are available [here](https://w3id.org/knowhow/queries).

## Sample SPARQL Endpoint

A sample SPARQL endpoint is available at [Dydra](https://w3id.org/knowhow/sparql). You can use [this URI](http://dydra.com/paolo-pareti/knowhow6/sparql) for federated queries. To get you started, [here](https://w3id.org/knowhow/queries) are some sample queries. **NOTE:** this endpoint exposes **only** a subset of the dataset, more specifically files: 

* *8of11_knowhow_wikihow*
* *9of11_knowhow_wikihow*
* *instruction set entities*
* *Process - Inputs*
* *Process - Outputs*
* *Process - Step Links*
* *wikiHow categories hierarchy*

## Statistics

* **23,033,490**: number of triples.
* **2,610,223**: number of labelled RDF nodes.
* **215,959**: number of instructions.
77% from wikiHow (datasets *1of11_knowhow_wikihow* to *9of11_knowhow_wikihow*) and 23% from Snapguide (datasets *10of11_knowhow_snapguide* to *11of11_knowhow_snapguide*).
* **255,101**: number of process inputs linked to 8,453 distinct DBpedia concepts (dataset *Process - Inputs*)
* **4,467**: number of process outputs linked to 3,439 distinct DBpedia concepts (dataset *Process - Outputs*)
* **376,795**: number of step links between 114,166 different sets of instructions (dataset *Process - Step Links*)

------

###### This dataset is partially based on original instructions from [wikiHow](http://www.wikihow.com/) and [Snapguide](https://snapguide.com/) accessed on the 16th of July 2014. It is licensed under the Creative Commons Attribution-NonCommercial 4.0 International [(CC BY-NC 4.0)](http://creativecommons.org/licenses/by-nc/4.0/) licence. DOI: http://dx.doi.org/10.7488/ds/1394

------

###### For any queries and requests contact: [Paolo Pareti](https://w3id.org/people/paolo)

------
