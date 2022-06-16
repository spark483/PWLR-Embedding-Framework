# PWLR-Embedding-Framework
This Github repository provides an exemplary python code which constructs collections of PWLR graph representations and use them to classify MUTAG, PTC-FR, BZR, and BZR-MD graph datasets. 

The results in Table 2 of the manuscript and Tables 4 and 8 of the manuscript can be obtained by running the “PWLR_main.ipynb” Jupyter notebook.

As for additional experiments, the explicit PWLR representations for all 0 <= k1,k2 < 30 can be stored in .npy files by running the “PWLR_Embedding.ipynb” Jupyter notebook. 

After the .npy files are stored, one may run graph classification results for other values of k1 and k2 by running the “PWLR_classification.ipynb” Jupyter notebook.

# Related Papers
"The PWLR graph representation: A Persistent Weisfeiler-Lehman scheme with Random Walks for graph classification"

Accepted to ICML Topology, Algebra, and Geometry in Machine Learning Workshop 2022

Authors: Sun Woo Park*, Yun Young Choi*, Dosang Joe, U Jin Choi, Youngho Woo+

*: (Sun Woo Park and Yun Young Choi made equal contribution as first authors)

+: (Corresponding Author: Youngho Woo)

# File List
- PWLR_main.ipynb

This file contains the “PWLR_main” function which performs graph classification tasks for the previously mentioned 4 datasets. This file imports the “PWLR_Embedding.ipynb” and “PWLR_classification.ipynb” notebooks.

- PWLR_main
  - name: name of the dataset in string. (Possible choices: “MUTAG”, “PTC_FR”, “BZR”, “BZR_MD”
  - data_type: specify whether the PWLR embedding framework processes discrete node labels (‘Discrete’) or continuous node attributes (‘Continuous’).
  - output_type: specify whether the PWLR embedding framework processes both discrete and continuous node attributes (‘both’) or not (‘single’).
  - k1_num: the number of WL iteration procedure (“k1” from the manuscript)
  - k2_num: the number of RW iteration procedure (“k2” from the manuscript)
  - embed_type: specify the type of PWLR representation: either the PWLR-H_i representations (embed_type=1) or the PWLR-OPT-H_i representations (embed_type=2).
  - entry_type: specify whether to use classes of components (H0,entry_type=0), classes of cycles (H1, entry_type=1), or both (H0+H1,entry_type=2) used for constructing PWLR representation.
  - grid_type: specify whether to utilize grid search for tuning hyperparameters of random forest classifiers.
  - feature_type: specify whether to compute feature importance obtained from using random forest classifiers.
- PWLR_Embedding.ipynb

This file contains the “GraphDataset” and “PWLR” classes which construct PWLR representations. Running the subscripts of the notebook in consecutive order creates a collection of .npy files under the “embed/dataset_name/~” folder. These .npy files store 900 collections of graph representations, obtained for all 0 <= k1, k2 < 30.
- PWLR_classification.ipynb

This file contains implementations of random forest classifiers for assessing the performance of PWLR representations. Please be aware that the “PWLR_Embedding.ipynb” Jupyter notebook must be implemented before running this notebook. The notebook imports the .npy files stored under the “embed” folder, and perform graph classification using the random forest classifier.
- “data” folder

This folder contains .gml dataset files for MUTAG, PTC_FR, BZR, and BZR_MD.
- “embed” folder

This folder contains PWLR-OPT H0 and PWLR-OPT H1 representations for BZR_MD datasets, as well as dataset folders for storing PWLR and PWLR-OPT representations for MUTAG, PTC_FR, BZR, and BZR_MD datasets. Please do not delete the folders within the “embed” folder, even though they are empty. After running the “PWLR_classification.ipynb” Jupyter notebook, the PWLR and PWLR-OPT representations will be stored inside the respective folders.

# Notes
- In case the “.gml” dataset files do not compile:

We attached PWLR-OPT H0 and PWLR-OPT H1 representations for BZR_MD datasets
as .npy files inside the “embed” folder. You may run the corresponding scripts under the subtitle “BZR_MD PWLR-OPT” inside the “PWLR_classification.ipynb” Jupyter notebook without running other notebooks.

- In case the “PWLR_main.py” notebook does not import other Jupyter notebooks:

Please make sure to install the nbimporter package. The corresponding python script is commented in the second cell of “PWLR_main.py” Jupyter notebook.The following python code constructs collections of PWLR graph representations and use them to classify MUTAG, PTC-FR, BZR, and BZR-MD graph datasets. The results in Table 2 of the manuscript and Tables 4 and 8 of the manuscript can be obtained by running the “PWLR_main.ipynb” Jupyter notebook.

As for additional experiments, the explicit PWLR representations for all 0 <= k1,k2 < 30 can be stored in .npy files by running the “PWLR_Embedding.ipynb” Jupyter notebook. After the .npy files are stored, one may run graph classification results for other values of k1 and k2 by running the “PWLR_classification.ipynb” Jupyter notebook.

# Datasets

All four data sets can be obtained from TU Dortmund Benchmark Data Sets for Graph Kernels (url: https://ls11-www.cs.tu-dortmund.de/staff/morris/graphkerneldatasets). 

The .gml data sets for MUTAG and PTC-FR can also be obtained from the github repository for "P-WL:A Persistent Weisfeiler-Lehman Procedure for Graph Classifications" by Rieck et al. (url: https://github.com/BorgwardtLab/P-WL)
