This repository contains all the probabilistic BDI models executable via BigraphER for SEFM'21 paper.

These models are the encodings of CAN lanugage for the BDI agents with different plan and intention selection strategies as follows

Plan Selection Strategies: 

	SMP: Selecting Most Preferred, 
	PSD: Preference Situational Distribution.

Intention Selection Strategies: 

	SMU: Selecting Most Urgent, 
	FIFO: First-In- First-Out, 
	RR: Round Robin, 
	PUSD: Pure Urgency Situational Distribution, 
	LUSD: Layered Urgency Situational Distribution, 
	OLUSD: Optimised Layered Urgency Situational Distribution

For example, SMP_SMU.big is the model with SMP for plan selection and SMU for intention selection.

To run the models, please first download the latest BigraphER from : https://uog-bigraph.bitbucket.io/index.html

To run them, simply do the command line: 

	bigrapher full -f svg -t index.svg -s . --solver=MCARD file.big 

for inspecting the entire transition.
	
To obtain the transtion file for PRISM, please simple do the command line: 

	bigrapher full -p file.tra -l file.csl --solver=MCARD bdi.big
	
For PRISM quantitative analysis, please go to PRISM website first for downloading: http://www.prismmodelchecker.org/download.php
	
Once obtaining the transition file for PRISM, please run the command line: 

	prism -dtmc -importtrans file.tra file.csl
	
Make sure you added the following properties of the interets in file.csl first 

	P = ?[F "box_1_success" & "box_2_success"];
	P = ?[F "box_1_success" & "box_2_failure"];
	P = ?[F "box_1_failure" & "box_2_success"];
	P = ?[F "box_1_failure" & "box_2_failure"];
