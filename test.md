This is the project code of CS5783 - Machine Learning course. The dependencies of the project is:

* tensorflow
* sklearn
* yaml
* numpy
* matplotlib
* os
* sys
* scipy
* random
* io
* csv
* imageio
* panda

The overview of the codes as follows:

1. Data Collection:
CFD Data Collection-ANSYS Fluent is used for the numerical simulation and time dependent data is obtained for the smapling window named-"exitnozzle". Data format is ASCII. 
CFD simulation is ran in HPC and the scripts files can be found in the same folder. 

2. DMD Algorithm:
_DMD_m_01_t_0001.py_ is used to run obtained the linear reduced order model result and merged with NLPOD(ML model) result for comparative analysis.

3. Data Preparation for ML algorithm:
_code.py_ is used to convert the data files into npz format for (input.yaml) input data for NLPOD. NewData is the saved the np files.

4. SVD for AE:
_svd.py_ is used to take the singular value decomposition of the CFD data/True data/Full order model (FOM).

5. ML algorithm:
_PODAE.py_ is used to train and test the AE and LSTM networks. The code work for train AE, test AE, train LSTM, and test LSTM depending on the _mode:_ option in input/input.yaml.


In order to run the code, please follow the order below:

* run _DMD_m_01_t_0001.py_ to obtain linear ROM of the CFD Data.
* run _code.py_ to convert the resultant data files into a format that following algorithms can read.
* run _svd.py_. This will take the singular value decomposition of the CFD data/True data/Full order model (FOM).
* change/make sure _mode:_ in input/input.yaml is in *nlpod* for training autoencoder (AE). (Please do not change the hyperparameters/model parameters if you are not sure what you are doing.)
* run _PODAE.py_ code to train the AE first. This will save the model to be used in the LSTM network.
* change _mode:_ in input/input.yaml to *nlpodtest* for testing AE.
* run _PODAE.py_ code again to test the AE. This will also create some figures in plot/ folder.
* change _mode:_ in input/input.yaml to *lstm* for training LSTM network.
* run _PODAE.py_ code to train the LSTM network. This will save the model.
* change _mode:_ in input/input.yaml to *lstmTest* for testing LSTM network.
* run _PODAE.py_ code again to test the LSTM network. This will also create some more figures in plot/ folder.
