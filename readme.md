[![Binder](https://mybinder.org/badge_logo.svg)]( https://mybinder.org/v2/gh/agstn/heatmaps_rlc/HEAD?urlpath=rstudio )


### Uncertainty in study planning
[Study data set](https://github.com/VIS-SIG/Wonderful-Wednesdays/tree/master/data/2022/2022-01-12). Presented on **January 12th, 2022** 

<img src="https://raw.githubusercontent.com/agstn/heatmaps_rlc/main/heatmaps_rlc.png" width="100%" height="100%">

### Details

Visualizing study planning uncertainty by interactive linked heatmaps. These heatmaps are an aid in determining sample size requirements and/or power for varying levels of Accrual Time, Follow-up Time [1st Heatmap] and Hazard Ratios, Hazard Rates for Sample Size Solution [2nd Heatmap] or Power, assuming a baseline model *  

```
baseline model: Accrual Time [24 months], Follow-up Time [6 months] for a Total Time [30 months]  with Hazard Ratio [0.775] and Hazard Rate [5%] 
with translate into a sample size of 9726 for 90% power  
using SAS PROC POWER twosamplesurvival test=LOGRANK 
proc power;
   twosamplesurvival test=LOGRANK   
   curve("Treatment")   = (0 12 24 36 48):(1 0.950 0.900 0.850 0.800) /* 5.0% 
   refsurvival = "Treatment"
   hazardratio =  0.775 
   accrualtime =  24 
   followuptime =  6 
   groupweights = (1 1)
   ntotal = . 
   sides = 2
   alpha = 0.05
   power = 0.90;
run;
```

By linking through these heatmaps we can investigate **5005** different scenarios. First, the user will click on the 1st heatmap to determine the assumptions concerning the study duration (Accrual, Follow-up Time), the title and remaining heatmaps will be updated accordingly. Second, by clicking on the 2nd heatmap, the user can investigate the sample size required to achieve 90% power. Also, if the user wants to examine the power for the baseline model, the 3rd heatmap can be used. Again, titles are updated following each selection. Finally, to make the code and visualization fully reproducible on a virtual and fixed environment I created a binder, which in short is a build of a docker image of my GitHub repository. 

These are the steps:

1-	Go to https://github.com/agstn/heatmaps_rlc  

2-	Press the binder launch badge  

3-	Wait a minute or two to get the image started  

4-	Once RStudio is launched click the `heatmaps_rlc.r` file in the bottom left pane  

5-	Then press Source  

6-	After it run, the Viewer will create the visualization, press in that pane the icon (box/arrow) to show the figure in a new window (expand)  

7-	The interactive chart is ready to be used, the user can also adjust each legend to their own needs (adjust the total sample, sample size and/or power to different baselines and ranges)  

For this challenge, my goal was two-folded. First to explore the vast possibilities of assumptions. Second, to explore the possibility of making everything fully reproducible so that anyone can access the code and made any changes in the cloud.
[Visualizing study planning uncertainty by interactive linked heatmaps ](https://hub.gke2.mybinder.org/user/agstn-heatmaps_rlc-so0stfvd/rstudio/p/348375e7/)

