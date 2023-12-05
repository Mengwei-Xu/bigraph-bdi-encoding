# This repository contains all the probabilistic BDI models executable via BigraphER for SoSyM-SEFM21-Specail Issue paper.

## The following is the list of instruction on how to reproduce the experiments given in the paper and how this repository is related to the paper. 

### 1. We have a list of selection strategies (and their abbreviations) given in the "**Table 1: Selection strategies**" in paper. 

#### Agent-level Rule Selection Strategies
* SIP: Select In Priority, 
* ProD: Progress Distribution.
	
#### Event/Intention Selection Strategies: 
* SMU: Selecting Most Urgent, 
* FIFO: First-In- First-Out, 
* RR: Round Robin, 
* UD: Urgency Distribution, 
* CUD: Conditioned Urgency Distribution, 
* OCUD: Optimised Conditioned Urgency Distribution.

#### Plan Selection Strategies: 
* SMP: Selecting Most Preferred, 
* PreD: Preference Situation.

### 2. The folder **Table_2_executable_models** contains all the relevant bigraph models to reproduce the results in **Table 2** in the paper. 

##### For example, SIP_SMU_SMP.big is the model with SIP for agent-level rule selection, SMU for event/intention selection, and SMP for plan selection.

###### The following is the step-by-step instruction on how to execute each model and perform resulting probabilistic analysis. 

1. To run the models, please first download the latest BigraphER from : https://uog-bigraph.bitbucket.io/index.html

2. To run them, simply do the command line: 
```
bigrapher full -f svg -t index.svg -s . --solver=MCARD file.big 
```

3. To obtain the transtion file for PRISM to inspect the entire transition. , please simple do the command line: 
```
bigrapher full -p file.tra -l file.csl --solver=MCARD bdi.big
```
	
4. For PRISM quantitative analysis, please go to PRISM website first for downloading: http://www.prismmodelchecker.org/download.php
	
5. Once obtaining the transition file for PRISM, please run the command line: 
```
prism -dtmc -importtrans file.tra file.csl
```
	
6. Make sure you added the following properties of the interets in file.csl first 
```
P = ?[F "box_1_success" & "box_2_success"];
P = ?[F "box_1_success" & "box_2_failure"];
P = ?[F "box_1_failure" & "box_2_success"];
P = ?[F "box_1_failure" & "box_2_failure"];
```

### 3. The folder **Table_3_executable_models** contains all the relevant bigraph models to reproduce the results in **Table 3** in the paper. 
It follows the exact same step as for table 2.

### 4. The folder **Figure_14_executable_models** contains all the relevant bigraph models to reproduce the results in **Figure 14** in the paper. 

This experiment essentially changes the failure rate of the standard bag from 10% to 90%, which simply requires tiny change of the weight number in the model and the rest of model remains the same.

For convinience of any reproduction experiments, however, I rename each model file with different failure rate and keep it as its own. And it follows the exect same step as previously detailed to run and analyse them. 

**Finally, any question in terms of reproducing these experiments, please drop me an email at Mengwei.Xu@glasgow.ac.uk.**
  


