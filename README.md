# Behavioral Analysis Preprocessing Pipeline (UB-COREDEM WP2.9)
Authors: Gloria Cecchini (MATLAB preprocessing scripts), Michael DePass (.mat to .csv Python script), Ignasi Cos (Experimental Design)
## Contents
1. MySQL database backup file (.sql) 
2. MATLAB scripts (.m) for behavioral data preprocessing
    - Import and organize .bhv2 MonkeyLogic files
    - Upload data to the MySQL database 
    - Read data from the MySQL database
    - Plot behavior data including decisions & oculometry
    - Export data to .mat file 
3. .mat to .csv Python conversion script, ideal for import to Pandas dataframe.
4. [Link to raw data](https://drive.google.com/drive/folders/1I9lFkNSw71a0NRWHtM_x7pKMZz-m4sxR?usp=sharing) and inputs/outputs for the scripts. 

### MATLAB Pipeline Instructions
0. Import empty database (MySQL_coredembcn_baseline.sql) to MySQL --- to create the DB.
1. Set working directory to directory containing Main.m
2. Open Main.m in MATLAB and execute. 
3. You will be prompted to select the folder where the raw data are saved.
    - Data collected at UB as well as inputs and outputs of the scripts can be found [here](https://drive.google.com/drive/folders/1I9lFkNSw71a0NRWHtM_x7pKMZz-m4sxR?usp=sharing). (Note: folders to be processed must be unzipped first!)
4. You will be prompted to provide your MySQL username as a string e.g. 'gloria'.
5. You will be prompted to input the 2 digit subject number of the folder to upload.
   - When you are done with the upload, input 1.
6. Continuing follow instructions in the prompts.
   - When asked "Do you want to include all participants?", this refers to whether you want to continue plotting all uploaded particpipants or a subset (array containing indices of desired subjects for plotting).
   - Note: Only last 18 participants have oculometry data. 
   
*Direct questions regarding MATLAB pipeline to gloria.cecchini@ub.edu*

### mat2csv
Input: aggregate .mat file (output from Main.m)
Output: Pandas-ready .csv file
1. Edit mat_file_name and csv_file_name variables as appropriate. 
2. Execute the script.

*Direct questions regarding mat2csv to michael.depass@ub.edu*

### Pipeline Flowchart
```mermaid
	flowchart LR
		A(.bhv2) -->|input| B{Main.m};
		B -->|output| C(.mat);
		C -->|input| D{mat2csv.py};
		D -->|output| E(.csv);
```
All processed data is available in the .mat file(s) exported by Main.m. If you wish to work with the data in another language, we recommend converting the .mat file(s) to a .csv file via mat2csv.py. 
### Example Output
Example decisions plotted for Horizons 0 and 1 of the Consequential task:
| Horizon 1                           |                           Horizon 2 |
|-------------------------------------|-------------------------------------|
|![](./img/sample_behavior_data_h0.png)   |![](./img/sample_behavior_data_h1.png)   |


Example Pandas DataFrame after conversion to .csv:
![](./img/dataframe.png)

### Experimental Design at UB
*Direct any questions regarding the experimental design to ignasi.cos@ub.edu*
