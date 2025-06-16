# GAP_Projection
This repo contains one Jupyter Notebook—`GAP - Share.ipynb`—that shows, step-by-step, how to predict **birth weight at delivery** from earlier-pregnancy ultrasound scans using the **Gestation-Adjusted Projection (GAP)** method and several published fetal-growth curves.

## What you get
* **Reusable functions inside the notebook**
  * `make_interp`* – builds a per-curve linear interpolator
  * `compute_predicted_bw_interp`* – applies the GAP formula to each record
  
* Median fetal weight tables for  
  * **Brenner** 
  * **WHO General**
  * **WHO Sex-specific**
  * **INTERGROWTH-21**

 ## Repo layout
 * GAP - Share.ipynb
 * README.md

## Using the functions in your own project
Before call the function compute_predicted_bw_interp
  1. Build your own variable of "ultra_days" and "deliv_days" based on your own dataset
  2. The estimated fetal weight by ultrasound in my dataset is called "f_weight", you can either change you variable to this name or change the function variable name before call it
  3. Same thing for the sex of the infants
Then Call the function:
There is a sample code to call the function:
merged['predicted_bw_brenner'] = merged.apply(compute_predicted_bw_interp, axis=1,args=('brenner',)).astype("Int64")
df["create new column of predicted bw"] = df.apply(compute_predicted_bw_interp,axis=1,args=('fetal curve you want to use',))

## Extending with new curves
1. Add a {week:int → median:int} dictionary at the top of the notebook.
2. Pass the new curve name to compute_predicted_bw_interp. That’s it.
