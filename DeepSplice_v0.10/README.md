# DeepSplice
A deep learning based splice junction sequence classifier.

Yi Zhang (yi dot zhang at uky dot edu)

## Manual

### 1. INPUT SPLICE JUNCTION SEQUENCE REPRESENTATION
A splice junction sequence is represented by four subsequences, the upstream exonic subsequence and downstream intronic subsequence at the donor site, and the upstream intronic subsequence and downstream exonic subsequence at the acceptor site. Each subsequence has the length of 30. Nucleotides in each sequence are represented through one-hot encoding, in which A, C, G, T and N are encoded by [0, 0, 0, 1] [0, 0, 1, 0] [0, 1, 0, 0] [1, 0, 0, 0] and [0.25, 0.25, 0.25, 0.25] respectively.

```
For example:
A raw splice junction sequence �TGCAGAGGACAACGCAGCTCCGCCCTCGCGGTGCTCTCCGGGTCTGTGCTGAGGAGAACGGGGTCTTGATGCTGTGGTCTTCATCTGCAGGTGTCTGACTTCCAGCAACTGCTGGCCTGT� 
is converted to 
�1,0,0,0,0,1,0,0,0,0,1,0,0,0,0,1,0,1,0,0,0,0,0,1,0,1,0,0,0,1,0,0,0,0,0,1,0,0,1,0,0,0,0,1,0,0,0,1,0,0,1,0,0,1,0,0,0,0,1,0,0,0,0,1,0,1,0,0,0,0,1,0,1,0,0,0,0,0,1,0,0,0,1,0,0,1,0,0,0,0,1,0,0,0,1,0,0,0,1,0,1,0,0,0,0,0,1,0,0,1,0,0,0,0,1,0,0,1,0,0,0,1,0,0,1,0,0,0,0,1,0,0,0,0,1,0,1,0,0,0,0,0,1,0,1,0,0,0,0,0,1,0,0,0,1,0,0,1,0,0,0,1,0,0,0,1,0,0,1,0,0,0,0,0,1,0,1,0,0,0,0,1,0,0,1,0,0,0,0,1,0,0,0,0,1,0,1,0,0,0,0,1,0,0,0,0,0,1,0,1,0,0,0,1,0,0,0,0,0,1,0,1,0,0,0,0,0,1,0,0,0,1,0,0,1,0,0,1,0,0,0,1,0,0,0,1,0,0,0,1,0,0,1,0,0,0,0,0,1,0,1,0,0,0,1,0,0,0,0,1,0,0,0,0,0,1,1,0,0,0,0,1,0,0,0,0,1,0,1,0,0,0,0,1,0,0,1,0,0,0,0,1,0,0,0,1,0,0,1,0,0,0,0,0,1,0,1,0,0,0,1,0,0,0,0,0,1,0,0,0,0,1,1,0,0,0,0,0,1,0,1,0,0,0,0,1,0,0,0,0,1,0,0,0,0,1,0,1,0,0,0,1,0,0,1,0,0,0,0,1,0,0,1,0,0,0,0,0,1,0,1,0,0,0,0,1,0,0,0,0,0,1,0,0,1,0,1,0,0,0,1,0,0,0,0,0,1,0,0,0,1,0,0,0,0,1,0,1,0,0,0,0,1,0,0,0,0,1,0,0,0,1,0,0,1,0,1,0,0,0,0,1,0,0,0,0,1,0,1,0,0,0,0,1,0,0,0,1,0,0,0,0,1,0,0,0,1,0,1,0,0,0,0,1,0,0,1,0,0,0�
```

An example of DeepSplice input file is �DeepSplice_v0.10/TestData/input.csv�. In the first line of the input CSV file, �10� indicates the number of input splice junction sequences, and �480� indicates the number of input features. In the following lines, there are ten input splice junction sequences.

### 2. RUNNING DEEPSPLICE FOR WHOLE GENOME SPLICE JUNCTION CLASSIFICATION FOR HUMAN ON PRETRAINED MODEL

```
python DeepSplice_pretrained.py <input_csv_file> <output_directory>
For example:
python DeepSplice_v0.10/PretrainedModelforHuman/DeepSplice_pretrained.py DeepSplice_v0.10/TestData/input.csv DeepSplice_v0.10/TestData/
```

### 3. OUTPUT
DeepSplice outputs the file �DeepSplice_v0.10/TestData/predictionResult.txt�, which indicates the predicted label of class, 1 for positive and 0 for negative.

## Citation
Zhang, Y., Liu, X., MacLeod, J.N. and Liu, J., 2016, December. DeepSplice: Deep classification of novel splice junctions revealed by RNA-seq. In *Bioinformatics and Biomedicine (BIBM), 2016 IEEE International Conference on* (pp. 330-333). IEEE.

DOI: [https://doi.org/10.1109/BIBM.2016.7822541](https://doi.org/10.1109/BIBM.2016.7822541)