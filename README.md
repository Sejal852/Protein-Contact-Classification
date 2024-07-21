# Protien Contact Classification
This project involves classifying contact information using a neural network implemented with Keras. The model takes input features related to contacts and classifies them into predefined categories.
# Project Context

Residue Interaction Networks are derived from protein structures based on geometrical and physico-chemical properties of the amino acids. RING is a software that takes a PDB file as input and returns the list of contacts (residue-residue pairs) and their types in a protein structure. RING contact types include:

- Hydrogen bonds (HBOND)
- Van der Waals interactions (VDW)
- Disulfide bridges (SBOND)
- Salt bridges (IONIC)
- π-π stacking (PIPISTACK) 
- π-cation (PICATION)
- π-pibond(PIHBOND)        
- Unclassified contacts

This project involves classifying contact information using a neural network implemented with Keras. The model takes input features related to contacts and classifies them into predefined categories.

# Repository Overview and Files


The repository is structured as follows, highlighting only pertinent files and directories:

```
      
🗎 contact_net.py: main python script. run for inference or training, specifying arguments.
🗎 model.py: python script containing the untrained model.
🗎 contacts_classification_keras.ipynb: Jupyter notebook of ContactNet.

```


# Dependencies 

Assuming that Python 3.x is already installed, ensure the following dependent Python libraries are installed on your machine before running the software:

- `biopython`
- `numpy`
- `pandas`
- `sklearn`
- `imblearn`
- `keras`
- `tensorflow`


For visualization after training, you will also need:

matplotlib
seaborn
To install all necessary dependencies, execute the following command: pip install biopython numpy pandas scikit-learn imbalanced-learn keras tensorflow matplotlib seaborn.

If python3 cannot locate these libraries, install them with: python3 -m pip install biopython numpy pandas scikit-learn imbalanced-learn keras tensorflow matplotlib seaborn



# Operating 
The software provides the following capabilities:

Perform instant predictions by loading the pretrained model.
Conduct thorough retraining of the model.

# Prediction Mode
Requirements: PDB code of the target protein (referred to as your_pdb_id).
To run the software by default, execute the following command in your terminal with arguments:

`python3 contact_net.py --predict --pdb your_pdb_id`

By default, the software will generate a .csv file containing a subset of preprocessed features used for inference by the model.
To include unprocessed features in the output .csv file, use the --unprocessedfeats argument.
To include all features from calc_features.py in the output .csv file, use the --full argument.
Usage Examples:

Run python3 contact_net.py --predict --pdb 5yj5 to generate the standard .csv output prediction file.
Run python3 contact_net.py --predict --pdb 5yj5 --unprocessedfeats to generate the .csv output prediction file with unprocessed features.
Run python3 contact_net.py --predict --pdb 5yj5 --full to generate the full-unprocessed-featured .csv output prediction file.
All generated files can be found in the data/output/ folder.

The software will download the PDB in .mmCIF format, compute its features using the calc_features.py script, and import the corresponding .tsv file. If the .tsv file is not found, the software will notify and terminate execution. Otherwise, it will preprocess the data and use the pretrained model to predict the contacts.

Upon completion, the software merges the DataFrame containing the protein's features with the one containing the probability distribution of each contact type, providing more information about the prediction confidence.

Finally, the software exports the final pdb_id_pred.csv file to the data/output/ folder.




# Training Mode

To initiate training of the model from scratch, execute the following command:

`python3 contact_net.py --train`



