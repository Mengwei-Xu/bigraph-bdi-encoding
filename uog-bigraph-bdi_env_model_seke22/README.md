# README #

This repository contains all the UAVs models executable via BigraphER for SEKE'22 paper.

These models are the encodings of CAN lanugage for the BDI agents with specification of dynamic external environment. 

To run the model, please first download the latest BigraphER from : https://uog-bigraph.bitbucket.io/index.html

To run it, simply do the command line:

> bigrapher full -f svg -t index.svg -s . --solver=MCARD SEKE_2022_BDI_Envs.big

To run the agent design in the Figure 5, set the `init design_figure_5`. Similarly, to run the corrected agent design in the Figure 6, set the `init design_figure_6`.

To generate the transition system, do the command line

> bigrapher full -p file.tra -l file.csl --solver=MCARD SEKE_2022_BDI_Envs.big

To use PRISM model checker, please go to PRISM website first for downloading: http://www.prismmodelchecker.org/download.php

Before using PRISM model checker, add the following propertie in `file.csl`. 

```
!E [ F ("belief_harsh_weather" & !"belief_at_base" & (X X "belief_at_base")) ];
A [ F "intention_completion"];
A [ "new_event_request"=>(F "new_event_assimilated")];
A [ "new_event_assimilated"=>(F "desire_committed")];

```

Then do the command line for property checking. 

> prism -dtmc -importtrans file.tra file.csl

To automatically identify the states which violated the first property above, we use the [filter function](http://www.prismmodelchecker.org/manual/PropertySpecification/Filters) for design in figure 5.


In detail, add the description `filter(print, filter(argmax, P = ? [ X X "belief_at_base" ], "belief_harsh_weather" & !"belief_at_base"));` in `file.csl`. 


Such a description essentially says that prints the states 

1. which satisfies the label `"belief_harsh_weather" & !"belief_at_base"` 

2. which have the highest probability (in our non-probabilistic case either 0 or 1) of having third state satisfying the label `"belief_at_base"`.





