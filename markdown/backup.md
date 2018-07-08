Tau-leaping interval
-----------------------------
<img src="images/it_gotl_sim_tau.svg" width="100%"/>



Model with CSC and division rate heterogeneity
-------------------------------------------------------------
<img src="images/it_gotl_csc_vdivrate_0012.svg" width="100%" style="margin-top: -20px"/>

Division rate heterogeneity induces clonal dominance, but does not reduce excessive clone loss


Model with CSC and division rate heterogeneity
-------------------------------------------------------------
* Division rate standard deviation determines clonal dominance
<img src="images/it_gotl_csc_vdivrate_var_sigma.svg" width="60%" style="margin: -10px"/>
* CSC&#x2080; and p&#x2081; determine clone loss
<img  src="images/fleft_heatmaps.svg" width="80%" style="margin: -10px"/>
* Best fit with 100% CSCs that only divide into CSCs.



Alternative division rate distribution
--------------------------------------------------------
<img src="images/it_gotl_sim_vdivrate_lognormal_var_growthrate.svg" width="100%"/>



Passage size reduces clone loss and clonal dominance
----------------------------------------------------------
<img src="images/sfig4.svg" width="50%">



Model does not reproduce clonal overlap
------------------------------------------------------------------
<img src="images/it_abm_sim_mut_vdivrate_364-484_major_clones.svg" width="70%" style="display: block;"/>

* No clonal overlap in the simulation because of initialization:
  * Simulation initialization: large population with clones distributed based on data at P0
  * Actual initialization: cells growth for 7-8 days after barcodes are inserted
* **There should be correlation between division rates for cells of the same clone**
