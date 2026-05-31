# engg2112_group_19

## File Descriptions
twosides_preprocessing.ipynb : maps TWOSIDES names to DrugBank IDs, removes duplicate rows, groups reactions into categories by finding the 50 most common reactions and grouping them (over a few repeats).
    DATA: http://tatonettilab-resources.s3-website-us-west-1.amazonaws.com/?p=nsides/

drugbank_smiles_extraction.ipynb: extracts DrugBank IDs and SMILES strings from the DrugBank full database XML file.

chembert_embeddings.ipynb: generates molecular embedding vectors for each drug using the pre-trained ChemBERTa model.

naive_bayes_baseline.ipynb: trains a Gaussian Naive Bayes classifier to predict the reaction category of a drug-drug interaction from ChemBERTa molecular embeddings.

svm_baseline_binary.ipynb: trains a Support Vector Machine classifier to predict whether or not a meaningful reaction of a drug-drug interaction from ChemBERTa molecular embeddings.

svm_baseline_pivot.ipynb: trains a Support Vector Machine classifier to predict the dominant reaction category of a drug-drug interaction from ChemBERTa molecular embeddings.


## File Run Order
1. drugbank_smiles_extraction
2. chembert_embeddings.ipynb
3. twosides_preprocessing.ipynb

4. ML Model

## Data Pipeline

full database.xml  →  drugbank_smiles_extraction.ipynb  →  drugbank_smiles.csv
                                                                ↓
                                                        chembert_embeddings.ipynb
                                                                ↓
                                                        chembert_embeddings.csv
                                                      ↓
TWOSIDES.csv  →  twosides_preprocessing.ipynb  →  twosides_edge_labels.csv
                                                      ↓
                                                  [ML Model]
                                          uses BOTH files together