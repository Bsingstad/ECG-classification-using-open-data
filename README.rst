**********************
FYS-STK4155 Project 3
**********************

.. image:: /img/12_lead_ecg_plot.png
**Figure 1:** This plot is made by using ecg plot [#]_  and the ECG data is from the PTB Diagnostic DB [#]_. 


Classification of 12-lead ECGs 
=================================================================
This project is based on the work we did in the  `PhysioNet/Computing in Cardiology Challenge 2020 <https://physionetchallenges.github.io/2020/>`_.  `This paper <https://iopscience.iop.org/article/10.1088/1361-6579/abc960>`_ describes the Challenge and `this paper <https://physionetchallenges.github.io/2020/papers/227.pdf>`_ discribes our contribution in this challenge.


Data:
=====
The data set in this project contains 43.101 ECGs and comes from six different sources. Table 1 show the six sources.

**Table 1:** *The table lists the six different sources used in the data set in this project*

+-----------------+---------------------------------------------------+
| Data set number | Name                                              |
+-----------------+---------------------------------------------------+
| 1               | China Physiological Signal Challenge 2018         |
+-----------------+---------------------------------------------------+
| 2               | China Physiological Signal Challenge 2018 Extra   |
+-----------------+---------------------------------------------------+
| 3               | St.Petersburg Institute of Cardiological Technics |
+-----------------+---------------------------------------------------+
| 4               | PTB Diagnostics                                   |
+-----------------+---------------------------------------------------+
| 5               | PTB-XL                                            |
+-----------------+---------------------------------------------------+
| 6               | Georgia 12-Lead ECG Challenge Database            |
+-----------------+---------------------------------------------------+

Preprocessing of data:
======================
The data used in two different ways by the models in this project. The first method, used by the Convolutional Neural Networks, is to use the as they are from the original dataset. The second method, used by the two ensemble models, is to extract features from the ECGs and and create a table with **n** rows and **m** columns were **n** = numbers of ECG recordings and **m** = number of features. The ECG-features are extracted by using an ECG-featurizer [#]_. The featurized data can be found `here <https://github.com/Bsingstad/FYS-STK4155-oblig3/blob/master/Data/ecg_data_with_labels.csv>`_ and the script for making the dataset is here: 
|makedataset|

.. |makedataset| image:: https://colab.research.google.com/assets/colab-badge.svg
   :target: https://colab.research.google.com/drive/1X5N_6gErP7--IDoN-AxW-aBbeYa4z-n7#scrollTo=mO_h0-9ebtCo  



Folder structure:
=================

 | Data
 | Hyperparameterresults
 | └── ECGopt11
 | Paper
 | └── Latex
 | Results
 | ├── ECG_results
 | └── Regression
 | Scripts
 | img
 

Get access to the data:
-----------------------
To get access to the data used in this study you can either download it from https://physionetchallenges.github.io/2020/#data or download the same data set from Kaggle. To use the codes in this repository you should sign up for a Kaggle account and get a Kaggle API token and use this to get access to the Kaggle data set from Google Colab. Google Colab Pro was used to get sufficient GPU power and enough runtime.
 
How to get your Kaggle API token:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
1. Log in to your `Kaggle account <https://www.kaggle.com/>`_ or sign up  `here <https://www.kaggle.com/account/login?phase=startSignInTab&returnUrl=%2F>`_ 
2. On the left side of the "edit profile"-button you click on the "Account"-option.   
3. Scroll down to the API-section and click "Create New API Token"-button. 
4. You will now have a file named kaggle.json. This is your API-token
5. You can upload the kaggle.json-file to the Google Colab notebook and then you are able to download datasets from Kaggle


   
10-fold cross-validated models:
-------------------------------
+--------------+---------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
| Model number | Model                                                               | Link to Google Colab Notebook                                                                                      | Link to Notebook on github                                                                                                                    |
+--------------+---------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
| 1            | FCN                                                                 | |FCN|                                                                                                              | `Notebook <https://github.com/Bsingstad/FYS-STK4155-oblig3/blob/master/Notebooks/Models/FCNPhysioNetChallenge2020.ipynb>`_                    |
|              |                                                                     |                                                                                                                    |                                                                                                                                               |
|              |                                                                     | .. |FCN| image:: https://colab.research.google.com/assets/colab-badge.svg                                          |                                                                                                                                               |
|              |                                                                     |    :target: https://colab.research.google.com/drive/17BLaVJkljEKIgfXw_StPm7YTkuOHsjl                               |                                                                                                                                               |
+--------------+---------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
| 2            | Encoder                                                             | |Encoder|                                                                                                          | `Notebook <https://github.com/Bsingstad/FYS-STK4155-oblig3/blob/master/Notebooks/Models/EncoderPhysioNetChallenge2020.ipynb>`_                |
|              |                                                                     |                                                                                                                    |                                                                                                                                               |
|              |                                                                     | .. |Encoder| image:: https://colab.research.google.com/assets/colab-badge.svg                                      |                                                                                                                                               |
|              |                                                                     |    :target: https://colab.research.google.com/drive/15V87RpZTI-ZRPlxhLHNQoVy9x3qdsXs4#scrollTo=1sq1Cs_SWQ0W        |                                                                                                                                               |
+--------------+---------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
| 3            | FCN + MLP                                                           | |FCN-MLP|                                                                                                          | `Notebook <https://github.com/Bsingstad/FYS-STK4155-oblig3/blob/master/Notebooks/Models/FCN_MLP_PhysioNetChallenge2020.ipynb>`_               |
|              |                                                                     |                                                                                                                    |                                                                                                                                               |
|              |                                                                     | .. |FCN-MLP| image:: https://colab.research.google.com/assets/colab-badge.svg                                      |                                                                                                                                               |
|              |                                                                     |    :target: https://colab.research.google.com/drive/1bVuZYcunlbLPIiUkCN9UKIE9AFcsxQrZ#scrollTo=L65YY9QqQZtf        |                                                                                                                                               |
+--------------+---------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
| 4            | Encoder + MLP                                                       | |Encoder-MLP|                                                                                                      | `Notebook <https://github.com/Bsingstad/FYS-STK4155-oblig3/blob/master/Notebooks/Models/Encoder_MLP_PhysioNetChallenge2020.ipynb>`_           |
|              |                                                                     |                                                                                                                    |                                                                                                                                               |
|              |                                                                     | .. |Encoder-MLP| image:: https://colab.research.google.com/assets/colab-badge.svg                                  |                                                                                                                                               |
|              |                                                                     |    :target: https://colab.research.google.com/drive/1eho24IylaAg20aIAav1ZmxgAGUU098D_                              |                                                                                                                                               |
+--------------+---------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
| 5 & 6        | Encoder + FCN (and Encoder + FCN + rule-based model)                | |FCN-Encoder|                                                                                                      | `Notebook <https://github.com/Bsingstad/FYS-STK4155-oblig3/blob/master/Notebooks/Models/Encder_FCN%2Brule_PhysioNetChallenge2020.ipynb>`_     |
|              |                                                                     |                                                                                                                    |                                                                                                                                               |
|              |                                                                     | .. |FCN-Encoder| image:: https://colab.research.google.com/assets/colab-badge.svg                                  |                                                                                                                                               |
|              |                                                                     |    :target: https://colab.research.google.com/drive/116seXHq2QwpuXUHUCXXLiAv-qYrsAIJB                              |                                                                                                                                               |
+--------------+---------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
| 7 & 8        | Encoder + FCN + MLP + (and Endcoder + FCN + MLP + Rule-based model) | |Encoder-FCN-MLP|                                                                                                  | `Notebook <https://github.com/Bsingstad/FYS-STK4155-oblig3/blob/master/Notebooks/Models/Encder_FCN_MLP%2Brule_PhysioNetChallenge2020.ipynb>`_ |
|              |                                                                     |                                                                                                                    |                                                                                                                                               |
|              |                                                                     | .. |Encoder-FCN-MLP| image:: https://colab.research.google.com/assets/colab-badge.svg                              |                                                                                                                                               |
|              |                                                                     |    :target: https://colab.research.google.com/drive/15V87RpZTI-ZRPlxhLHNQoVy9x3qdsXs4#scrollTo=1sq1Cs_SWQ0W        |                                                                                                                                               |
+--------------+---------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
| 9            | Ensemble model - 12 leads                                           | |ensemble12lead|                                                                                                   | `Notebook <https://github.com/Bsingstad/FYS-STK4155-oblig3/blob/master/Notebooks/Models/EnsembleModel2lead.ipynb>`_                           |
|              |                                                                     |                                                                                                                    |                                                                                                                                               |
|              |                                                                     | .. |ensemble12lead| image:: https://colab.research.google.com/assets/colab-badge.svg                               |                                                                                                                                               |
|              |                                                                     |    :target: https://github.com/Bsingstad/FYS-STK4155-oblig3/blob/master/Notebooks/Models/EnsembleModel12lead.ipynb |                                                                                                                                               |
+--------------+---------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
| 10           | Ensemble model - 2 leads                                            | |ensemble2lead|                                                                                                    | `Notebook <https://github.com/Bsingstad/FYS-STK4155-oblig3/blob/master/Notebooks/Models/EnsembleModel12lead.ipynb>`_                          |
|              |                                                                     |                                                                                                                    |                                                                                                                                               |
|              |                                                                     | .. |ensemble2lead| image:: https://colab.research.google.com/assets/colab-badge.svg                                |                                                                                                                                               |
|              |                                                                     |    :target: https://github.com/Bsingstad/FYS-STK4155-oblig3/blob/master/Notebooks/Models/EnsembleModel2lead.ipynb  |                                                                                                                                               |
+--------------+---------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+




Plot the cross-validation results:
----------------------------------
The results from the cross-validated models can be plotted with this notebook |plot|.
dddd

ddd

.. |plot| image:: https://colab.research.google.com/assets/colab-badge.svg
   :target: https://github.com/Bsingstad/FYS-STK4155-oblig3/blob/master/Notebooks/CVplot/boxplot.ipynb

Contains the report

Latex:
^^^^^^
Latex source files

Results:
--------
The folder contains plots from the various notebooks

ECG_results:
^^^^^^^^^^^^
Results related to the PTB-XL data set 

Regression_results:
^^^^^^^^^^^^^^^^^^^
Results related to the data set generated by Franke's function
     
Scripts:
--------
Files containing Python scripts used in the notebooks

img:
----
Contains images used in README-file

       
License
------------

Licensed under the `Apache 2.0 License`_

.. _Apache 2.0 License: http://www.apache.org/licenses/LICENSE-2.0

.. _NOTICE.txt: https://github.com/nedbat/coveragepy/blob/master/NOTICE.txt

.. _Apache License Version 2.0: http://opensource.org/licenses/Apache-2.0

.. |Apache2.0 license| image:: https://img.shields.io/badge/License-Apache%202.0-blue.svg
   :target: https://opensource.org/licenses/Apache-2.0
   
   


To be able to reproduce the csv-file with ECG-features, you can use this Notebook hosted on Google Colab. 
You will need a kaggle API-token to be able to access the 7 data sets that is used to make the csv-file:

https://colab.research.google.com/drive/1X5N_6gErP7--IDoN-AxW-aBbeYa4z-n7?usp=sharing

+---------------+------------------------------------------------------------------------------------------+
|               | Language                                                                                 |
+---------------+------------------------------------------------------------------------------------------+
| Code          | |made-with-python|                                                                       |
|               |                                                                                          |
|               | .. |made-with-python| image:: https://img.shields.io/badge/Made%20with-Python-1f425f.svg |
|               |    :target: https://www.python.org/                                                      |
+---------------+------------------------------------------------------------------------------------------+
| Documentation | |made-with-latex|                                                                        |
|               |                                                                                          |
|               | .. |made-with-latex| image:: https://img.shields.io/badge/Made%20with-LaTeX-1f425f.svg   |
|               |    :target: https://www.latex-project.org/                                               |
+---------------+------------------------------------------------------------------------------------------+

References:
-----------

.. [#] ECG plot: https://github.com/dy1901/ecg_plot
.. [#] PTB Diagnostic DB: Bousseljot R, Kreiseler D, Schnabel, A. Nutzung der EKG-Signaldatenbank CARDIODAT der PTB über das Internet. Biomedizinische Technik, Band 40, Ergänzungsband 1 (1995) S 317
.. [#] ECG-Featurizer: https://github.com/ECG-featurizer/ECG-featurizer




