# Protein Function Prediction

### About the Dataset

#### File Description

Gene Ontology: The ontology data is in the file `go-basic.obo`. This structure is the 2023-01-01 release of the GO graph. This file is in OBO format, for which there exist many parsing libraries.
```
subontology_roots = { 'BPO':'GO:0008150',
                      'CCO':'GO:0005575',
                      'MFO':'GO:0003674' }

```

Training sequences: train_sequences.fasta contains the protein sequences for the training dataset. The train_sequences.fasta file will indicate from which database the sequence originate.

Labels: train_terms.tsv contains the list of annotated terms (ground truth) for the proteins in train_sequences.fasta. The first column indicates the protein's UniProt accession ID, the second is the GO term ID, and the third indicates in which ontology the term appears.

Taxonomy: train_taxonomy.tsv contains the list of proteins and the species to which they belong, represented by a "taxonomic identifier" (taxon ID) number. The first column is the protein UniProt accession ID and the second is the taxon ID.

Information accretion: IA.txt contains the information accretion (weights) for each GO term. These weights are used to compute weighted precision and recall, as described in the Evaluation section.

#### Files

- **train_sequences.fasta** - amino acid sequences for proteins in training set.
- **train_terms.tsv** - the training set of proteins and corresponding annotated GO terms.
- **train_taxonomy.tsv** - taxon ID for proteins in training set.
- **go-basic.obo** - ontology graph structure.
- **testsuperset.fasta** - amino acid sequences for proteins on which the predictions should be made.
- **testsuperset-taxon-list.tsv** - taxon ID for proteins in test superset.
- **IA.txt** - Information Accretion for each term. This is used to weight precision and recall.

### Folder Structure

``` 
protein-function-prediction
	/data
	    /Train
	        /go-basic.obo
	        /train_sequences.fasta
	        /train_taxonomy.tsv
	        /train_terms.tsv
	    /Tests (Targets)
	        /testsuperset-taxon-list.tsv
	        /testsuperset.fasta
	    /IA.txt
	/t5_embeds
        /test_embeds.npy
        /test_ids.npy
        /train_embeds.npy
        /train_ids.npy
	/protein_function_prediction.ipynb
```

### Steps to Run and Execute the Code:

1. Clone the repository.
2. Download the `t5_embeds` embeddings from [here](https://www.kaggle.com/datasets/sergeifironov/t5embeds).
3. Check the folder structure is as mentioned above or make changes to the data import path in the ipynb file.
4. Execute the cells one by one.

### Note

- The dataset `data` is obtained from CAFA-5.
- The `final_output.tsv` file generated is large in size therefore it is not commited. Execute the cells to obtain the test set prediction.