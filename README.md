# SensoHapt

## Description
**SensoHapt** is an application targeted at providing an easy-to-use experiment environment 
for performing experiments involving 3DSystems haptic devices and ATI force sensors with stereoscopic 3D support.

Developed by Gilles Meyhi & Elias Stalpaert as part of their thesis pursuing a MSc degree in Engineering Technology: Electronics-ICT at KULeuven.

## Experiment configuration
Experiments are configured using a .xml file.
With possible elements being experiment, trial, event and trial features with their corresponding attributes.
(see given ExperimentConfig.xml for more help)


## Build requirements
Make sure the [OpenHaptics 3.5 toolkit](https://3dssupport.microsoftcrmportals.com/knowledgebase/article/KA-03459/en-us) and
[OpenHaptics Phantom Device Driver v5.1.7](https://3dssupport.microsoftcrmportals.com/knowledgebase/article/KA-01460/en-us) and
[ATICombinedDAQFT .NET Class Library](https://www.ati-ia.com/Products/ft/software/daq_software.aspx) are installed on the build machine.

- No hardware build (debug purposes): make sure the preprocessor directive 'NO_HARDWARE_DEBUG' is defined in stdafx.h at compile-time.

- Hardware build (normal):  make sure the preprocessor directive 'NO_HARDWARE_DEBUG' is NOT defined in stdafx.h at compile-time.

## Using the application
After starting the application using the built executable, the application will load the last given configuration .xml if applicable.
Otherwise, it will ask the user to select one using the Load Experiment button.

An overview of the configuration belonging to the .xml is provided using a tree-view on the main window.

The number of current experiment subject can be put in using the number counter on the main window.

Users can configure output paths and hardware details using the Settings-window accessed by the Settings-button on the main window.

After pushing the Run-button, the experiment will start. After completion, the main window will reappear, giving the possibility to redo the experiment.

### Settings

- Haptic Device Name: name of the haptic device as is recognized by the 3DSystems Phantom HD drivers

- DAQ Name: name of the used ATI DAQ as is recognized by DAQ software (like NIDAQ)

- Calibration files: files containing the calibration matrices for the transducers
(look at given FT8568.cal and FT8569.cal files for more help)

- Output paths: paths specifying output folders for the experimental data .csv's

### Output files
Experimental data is output in 3 files:

- Answers: .csv containing the answers of the subject belonging to an experiment run

- TrialData: .csv containing periodical measurements (period given by sampling rate) of haptic/force sensor measurements for further analyzation.

- ExperimentDetails: .csv containing information about the past experiment (which trials of the .xml config where used in what order)
(only important when random_enabled in .xml config file)

If an output file with the same subject of the same experiment already exists, it will be overwritten.