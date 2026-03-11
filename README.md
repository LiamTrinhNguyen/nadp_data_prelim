


# NADP_NTN_PRELIM Project
__author__ = 'Liam TrinhNguyen'
__contributors__ = ['N/A']
__email__ = [ 'LiamTrinhNguyen@gmail.com or TrinhNguyen@wisc.edu']
__version__ = ['preLim v0.1.0']
The data_prelim package is a headless Python pipeline engineered to automate the preliminary review of NTN laboratory data. It extracts data directly from the SQL Server database, runs vectorized anomaly detection (including sample date gap and overlap checks), evaluates chemical thresholds, and compiles the findings into a human-readable Excel report for final technician sign-off.


Key Features: 
The pipeline executes a strict 6-phase data engineering workflow:

Phase 1: Gap & Overlap Detection: Analyzes chronological boundary records up to 90 days out to identify missing or overlapping sample windows.
Phase 2: NTN1 Statistics Review: Aggregates and evaluates core network statistics.
Phase 3: Chemical Status Checks: Flags samples exceeding defined chemical thresholds.
Phase 4: TOTP Reload: Synchronizes and reloads TOTP data.
Phase 5: Master Data Combination: Merges flags, null values, and anomalies into a single optimized master DataFrame.
Phase 6: Report Generation: Exports a consolidated .xlsx file for interactive human review, alongside an optimized .parquet backup.

## Setup
1.  **Requirement**

    - SQL permissions to connect to the specific database.

    - The pre-compiled .whl file.

    - A .env file containing the output path, thresholds, driver, and server name.

    - Optional: Anaconda or Miniconda (Recommended for environment management, If not using conda skip step 2 and 3).

2.  **Create a Virtual Environment (optional): due to versioning control**
    This application can be deployed on any machine using a Python virtual environment. Installing the .whl file will automatically download and install all required dependencies (e.g., pandas, numpy).

    Open the Anaconda/Miniconda prompt and initialize it if you haven't already:    

    - after installing Anaconda or miniconda, open Anaconda prompt/ miniconda prompt:
        ```bash
        conda inital
        ```

    - close anaconda prompt/ miniconda prompt
    
    - open CMD windows:
        ```bash
        conda --version #this code to check if the conda install successful or not
        conda env list #get all available environments of the machine, 
        ```
    
    -  the result should return with an env such as: 
        ```bash
        # conda environments:
        #
        base                     C:\Program Files\ArcGIS\Pro\bin\Python
        arcgispro-py3            C:\Program Files\ArcGIS\Pro\bin\Python\envs\arcgispro-py3
        ```
    - clone the arcgispro-py3, where 'arcgispro-py3-clone' can be anyname of user chooses:
        ```bash
        conda create --name arcgispro-py3-clone --clone arcgispro-py3
        ```
    
2.  **Activate the Environment:**
    - On CMD Windows:
        ```bash
        conda env list #get all available environments of the machine, 
        ```
    
    -  the result should return with an env such as: 
        ```bash
        # conda environments:
        #
        base                     C:\Program Files\ArcGIS\Pro\bin\Python
        arcgispro-py3            C:\Program Files\ArcGIS\Pro\bin\Python\envs\arcgispro-py3
        arcgispro-py3-clone   *  C:\Users\User_name\AppData\Local\ESRI\conda\envs\arcgispro-py3-clone
        ```
    - after confirming that clone env is there, activate env:
        ```bash 
        conda activate arcgispro-py3-clone
        ```
    -  the result should return with an env such as: 
        ```bash
        (arcgispro-py3-clone) C:\> # which indicated that the machine entered the clone env where the name of the env is in the ()
        ``` 

3.  **Install Data_prelim file:**

    - Navigate to the folder containing your .whl file. Because this package is "Pure Python" with no compiled C/C++ code, it can run on any operating system.
  
    ```bash
    (arcgispro-py3-clone) K:\>pip install data_prelim-0.1.0-py3-none-any.whl
    ```
    to confirm the package has successful install

    ``bash
    (arcgispro-py3-clone) K:\>pip show nadp_tdep
    Name: data_prelim
    Version: 0.1.0
    Summary: "Laboratory data review pipeline for NADP/NTN."
    Home-page: https://github.com/LiamTrinhNguyen/nadp_data_prelim.git
    Author: Liam TrinhNguyen
    Author-email: Liamtrinhnguyen@gmail.com
    License: Proprietary / NADP Internal License
    ```

## Configuration

    Caution: Beware of the hidden files and folders, since some files start with '.'
            Make sure to show all hidden files first, then proceed.
            - Go to the directory that is working with.
            - On Windows, hidden files and folders are displayed  by navigating to the file explorer's 'view' tab,
            then selecting 'options' and 'change folder and search options'. In the 'view' tab of the dialog box,
            check'shows hidden files, folders, and drives' and click 'ok'


1.  Create a `.env` file by copying the example template to folder containing your .whl file or create new folder. This file will hold your local configuration.
    ```bash
    # On Windows (in Command Prompt)
    copy .env.example .env

    ```

2.  Open the new `.env` file and change those keys to the correct data in and out path, which link to the folder in ##Input Data Requirements below

```bash
WSLH_OUTPUT_DIR=/NTN_review_2026/testing_ouput_NTN2026/ #change this 
WSLH_THRESHOLD=0.05 # this should keep
WSLH_THRESHOLD_EXTREME=0.30 #this should keep
WSLH_DRIVE = ODBC Driver 17 for SQL Server #change this, if using the WSLH keep this one
WSLH_SERVER =     # change this to the correct name of the server
```




## Usage
Run from CMD or terminal with give input from prompt:
Redirect to the project's root directory that contains the .env file from CMD or terminal
(optional: activate the virtual environment or use the base one. But make sure you are using the environment in which the package was installed; Else, it will not work.


    ```bash
    (arcgispro-py3-clone) C:\> data_prelim # this code will access the Python interpreter on the selected virtual environment 
     # then follow the prompt 
    ```
     
## Credits

**Software Architecture & Implementation**
* **LIAM TRINHNGUYEN** (liamtrinhnguyen@gmail.com) 


**Copyright**
* Copyright © 2024 National Atmospheric Deposition Program (NADP_NTN network).
* Licensed under: read license Tab 
