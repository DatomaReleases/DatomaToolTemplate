# Datoma Python-based tool template
This document will guide you to migrate your Python tool to Datoma.

## What can you find on this folder?
There are eight main files:
- **.gitignore**: No need to modify this file, it will keep the folder clean of unnecessary files.
- **datomaconfig.yml**: You need only modify line **16**, change the `taskname` parameter to suit your project. 
    - If your main python script has a name different than **"script.py"**, change line **19** accordingly.
    - If the folder where your code outputs the results file is not named "**results**", change line **20** accordingly.
    - Keep in mind that the field on line **25** will be used later.
- **description.taskname.md**: You need to modify this file's name and change "taskname" for the name you defined on the previous file (line **16**).
    - Then, add a description and citation.
- **Dockerfile**: This file should be modified according to the needs of your tool. You can modify the base image and the dependencies installed. Also, the name od the python script can be modified if you wish. If your project requires additional files, please copy them to the **/app/** directory as you can see on line **8**.
    - To test that the project works, we recommend that you also copy an input file to the **/app** directory.
- **install_jobrunner_and_run.sh**: This file should only be modified if you have to set some environment variables (as shown on the line **7** example).
    - While testing, you will need to comment line 4 and also change line **9** for **python script.py** or similar.
- **install_jobrunner.py**: This file doesn't have to be modified.
- **layout.taskname.json**: This is the file used on Datoma's web to specify the parameters and attach the input files. Modify according to your project's needs.
    - Please, modify the filename, replacing `taskname` for the same name you have already defined on **datomaconfig.yml**.
    - The `key` parameter (line **24**) must be the same as the one on **datomaconfig.yml** (line **25**). 
- **script.py**: This is a mere example. The part you need to keep is the `datoma_entrypoint()` function declaration (line **3**).
    - Line **8** shows how to get the filename of the input file.
    - Line **9** shows how to get the value of a parameter.
    - Line **10** exemplifies how to get the number of cores that are available for this experiment.
    - When testing, we recommend to set up a main on the file that calls for the `datoma_entrypoint()` function.
    - While testing, we also recommend to modify proprietary functions such as `get_vcpu()`, since they only work on Datoma's infrastructure.

## How to test?
1. Inside this template's folder, execute the command `docker build -t toolname`
2. Then, run `docker run --rm toolname`
    - Alternatively, you can run `docker run --rm -it --entrypoint="bash" toolname` to run the container interactively.
3. If you have any issue while in this process, you can contact us at XXXXXXXXXX
4. When your project is working, please forward it to the Datoma team at XXXXXXXXXX