Intratumoral heterogeneity
----------------------------------------------------------
<img src="images/jamal-hanjani2015_2.png" width="50%" style="margin-bottom: 0px; display:block">
<div style="margin-bottom: 20px; font-size: .5em; text-align: center">Image from Jamal-Hanjani *et al.*, Clin. Canc. Res., 2015</div>

- Cells within the same tumor vary:
  - variation in environment may cause difference in phenotype
  - variation in genotype/epigenetics may cause difference in phenotype  
- Different clones respond differently to treatment


Study intratumoral heterogeneity with barcoding
------------------------------------------------------------------

- construct with random base pair sequence

<img src="images/barcode_vector.svg" width="40%" style="display:block"/>

- construct is inserted, e.g. with a virus vector

<img src="images/barcoding_diagram.svg" width="80%" style="margin-left:80px"/>

<div style=" display: flex; justify-content: center;">
  <div style="text-align: left; font-size: 55%; width:70%;"/>
  Based on [Porter *et al.* 2014. “Lentiviral and Targeted Cellular Barcoding Reveals Ongoing Clonal Dynamics of Cell Lines in Vitro and in Vivo.” Genome Biology 15 (5): R75.](https://genomebiology.biomedcentral.com/articles/10.1186/gb-2014-15-5-r75)
  </div>
</div>


Iterated growth & passage experiment
-----------------------------------------------------------
<img src="images/setup.svg" height="250" style="display:block"/>
- Preparation
  - Barcodes are inserted in the DNA using a lentiviral vector
  - Infected cells are selected (using a GFP tag) and grown
  - Three cell populations, each containing 3&#x22C5;10&#x2075;, cells are taken
- Experiment (three biological replicates)
  - Each population grows for 3 days, after which 4&#x22C5;10&#x2076; are present
  - 3&#x22C5;10&#x2075; cells are passed on to the next generation
  - growth & passages is repeated 30 times
  - samples taken at passages 10, 20, and 30

<div style=" display: flex; justify-content: center; margin-top:50px">
  <div style="text-align: left; font-size: 55%; width:70%;"/>
  Based on [Porter *et al.* 2014. “Lentiviral and Targeted Cellular Barcoding Reveals Ongoing Clonal Dynamics of Cell Lines in Vitro and in Vivo.” Genome Biology 15 (5): R75.](https://genomebiology.biomedcentral.com/articles/10.1186/gb-2014-15-5-r75)
  </div>
</div>


Iterated growth & passage experiment
-----------------------------------------------------------
We re-analyzed the experiments from [Porter *et al.* (Gen. Biol., 2014)](https://genomebiology.biomedcentral.com/articles/10.1186/gb-2014-15-5-r75), using the FASTQ files in the NIH Sequence Read Archive that were published with the paper.

<img width="100%" src="images/K562_all.svg">

* K562 cell (chronic myelogenous leukemia cell line)
* Clones disappear and clonal dominance increases

<div class="fragment" style="text-align:center;width:70%;margin:0 auto;margin-top:20px"><b> What mechanism explains clone loss and the development of clonal dominance? <b></div>



Computational model of simple growth & passage
------------------------------------------------------------------
<img data-src="images/setup.svg" height="250" style="display:block;"/>
* Initialization
  * ~12.000 clones with size $c_i$ and $\sum \_i c_i = 3 \cdot 10^5$.
  * Clone sizes assigned to fit the experimental data.
* Growth
  * Each cell grows with a given rate $r_i$
  * Growth continues until $\sum \_i c_i = 4 \cdot 10^6$
* Passage
  * $3 \cdot 10^5$ cells are taken randomly and passed to the next generation


Simulations with stochastic growth & passage
------------------------------------------------------------------
* All cells growth with rate $r$
  * deterministic: $c_i(t+\Delta t) = c_i(t) e^{r \Delta t}$
  * stochastic: $c_i$ evolves with &#x03C4;-leaping Gillespie algorithm
<div style="margin:0 auto; text-align:center">
<img data-src="images/simple_growth_all.svg" width="100%" style="margin-left:-250px"/>
* Clones disappear at a rate similar to that *in vitro*
* Clonal dominance does not develop



Source of intratumoral heterogeneity
-----------------------------------------------
<div style="position:relative; width:100%;  margin-left: auto; margin-right: auto; text-align: center; margin-top: 30px" >
  <div style="position:absolute;background: white;width:100%;height:600px">
  <img src="images/CSC_vs_stochastic_vert.svg" width="100%"/>
  <div style="font-size: .5em; text-align: center; margin-bottom: 20px">Image adapted from https://en.wikipedia.org/wiki/Tumour_heterogeneity</div>
  </div>
</div>


Model with cancer stem cells
-------------------------------------------------------------
<div style="text-align: center; font-size: .5em">
<img src="images/csc_model.svg" width="80%" style="display:block"/>
model based on Weekes *et al.*, Bull. Math. Biol., 2014
</div>

<div style="margin-top:60px">
  <div style="float:left; width:58%; margin-top:15px">
    <ul>
      <li>Parameterization based on analytical solution</li>
      <li> Monotonic growth for p&#x2081; > p&#x2083; </li>
      <li> Population growth rate depends on r<sub style="font-size: .8em">DC</sub> and maximum DC age (M)</li>
    </ul>
  </div>
  <div style="float:left;">
  <img src="images/weekes_model_pars_heatmap_YlOrRd_r.svg" width="380px"  style="float:right; margin-top: -60px"/>
  </div>
</div>


Model with cancer stem cells
-------------------------------------------------------------
<img src="images/it_gotl_csc_altpar_all.svg" width="100%"/>
<ul>
  <li>Cancer stem cells do not induce clonal dominance</li>
  <li>Almost all clones disappear</li>
</ul>


Model with cancer stem cells
-------------------------------------------------------------
<img src="images/it_gotl_csc_fleft_heatmaps.svg" width="75%" style="margin-top: -20px;"/>
<img src="images/it_gotl_csc_gini_heatmaps.svg" width="75%" style="margin-top: -20px;"/>



Source of intratumoral heterogeneity
------------------------------------------------------------------
<div style="position:relative; width:100%;  margin-left: auto; margin-right: auto; text-align: center; margin-top: 30px" >
  <img data-src="images/CSC_vs_stochastic_2.svg" width="100%"/>
  <div style="font-size: .5em; text-align: center; margin-bottom: 20px">Image adapted from https://en.wikipedia.org/wiki/Tumour_heterogeneity</div>
</div>
* Clonal evolution: division rate mutation
* Mutation requires tracking of individual cells


Agent based model (ABM) with with clonal evolution
-------------------------------------------------------------
* Cell $i$ has a division rate $r_i$ and a barcode.
* Initial variation to mimic evolution before experiment:
  * $r_i = rY$ with $Y$ taken from &#x1d4a9; (1,&sigma;<sub>r</sub>&#x00B2;)
* Division
  * division rate mutates: $r \_\text{child} = r \_\text{parent} X $ with $X$ taken from &#x1d4a9; (1,&sigma;<sub>m</sub>&#x00B2;)
* Division rate increases during the experiment
    <img src="images/it_abm_sim_mut_vdivrate_0792_divrates.svg" width="60%"/>


Iterated growth & passage with clonal evolution
-------------------------------------------------------------
* Clone loss increases with division rate variation
<img src="images/it_abm_sim_mut_vdivrate_1-120_heatmap_fleft.svg" width="85%" style="margin-bottom: -50px; margin-top: -20px;">

* Gini coefficient increases with division rate variation
<img src="images/it_abm_sim_mut_vdivrate_1-120_heatmap_gini.svg" width="85%" style=" margin-top: -20px;">



Matching ABM to *in vitro* results
------------------------------------------------------------------
* Maximum likelyhood estimation that includes:
  * P10, P20, and P30
  * 3 replicates
  * Percentage of remaining clones and/or Gini coefficient
* 3 data sets
  * K562 cells
  * monoclonal K562 cells
  * HeLa


Matching ABM to *in vitro* results for K562
------------------------------------------------------------------
<img src="images/it_abm_sim_mut_vdivrate_364-484_fit.svg" width="90%" style="float:left"/>

Results for best fit for Gini coefficient
<img src="images/it_abm_sim_mut_vdivrate_364-484_best_fit.svg" width="90%" style="float:left"/>


*In vitro* results for monoclonal K562
-------------------------------------------
* monoclonal K562 cell line is derived from a single cell

<img src="images/K562_VS_clonalK562.svg" width="75%"/>

* Less clone loss compared to K562 cell line
* No development of clonal dominance
* Expected model parameter changes to match monoclonal K562:
  * Less initial variation &#x21d2; lower &sigma;<sub>r</sub> than for K562
  * Same cell type &#x21d2; similar &sigma;<sub>m</sub> as with K562


Matching ABM to monoclonal K562 results
----------------------------
* Changes as expected for best fit (Gini coefficient)
<img src="images/it_abm_sim_mut_vdivrate_fit_clonalK562_metrics.svg" width="90%"
style="margin-left=50px; margin-top:-20px; margin-bottom:-30px"/>

* Clone loss is hard to match (min(MLE) = ~2000)
* Gini coefficient matches better (min(MLE) = ~5)

<img src="images/it_abm_sim_mut_vdivrate_best_fit_clonalK562.svg" width="80%" style="margin-left:50px; margin-top:-20px"/>


*In vitro* results for HeLa cells
--------------------------------------------
<img src="images/K562_VS_HeLa.svg" width="75%"/>

* Clone loss starts late
* Clonal dominance develops similar to K562 cell line


Matching ABM to HeLa results
------------------------------------------
<img src="images/it_abm_sim_mut_vdivrate_fit_HeLa_metrics.svg" width="80%"/>

* Clone loss is hard to match
* Gini coefficient matches better

<img src="images/it_abm_sim_mut_vdivrate_best_fit_HeLa.svg" width="80%"/>


*In vitro* clone loss may be underestimated
---------------------------------------------------------------
* Minimal clone loss for a model without any division rate variation
* Clone loss observed with clonal K562 is larger than that in a simulation without division rate variation
<img src="images/cK562_vs_simple_growth.svg" width="100%"/>


*In vitro* clone loss may be underestimated
----------------------------------------------
* Data may contain *spurious reads*
* Susceptibility for *spurious reads* is correlated to sequence

<img src="images/sfile1_fig1.svg" width="40%"/>
<img src="images/sfile1_fig2.svg" width="50%"/>

* Simulation with spurious reads indicates that:
  * Adding spurious reads reduces clone loss such that *in vitro* observations are reproduced
  * Adding spurious reads increases the Gini coefficient, but *in vitro* observations can still be reproduced



Conclusion
------------------------------
* Model based on cancer stem cells does not match *in vitro* iterated growth and passage
* Model based on clonal evolution can match *in vitro* iterated growth and passage
  * Model fits well to changes in clone size distribution observed *in vitro*
  * Model predicts same mutation dynamics for polyclonal and monoclonal K562 cells
* Non-matching clone loss for monoclonal K562 and HeLa may be explained by spurious reads



What about the ecosystem?
--------------------------------
* *In vivo* lineage tracing shows various clone size dynamics
  <div style="margin-bottom: 0px">
    <img src="images/zomer2013brief_fig3.png" width="850px"/>  
	<div style="font-size: .5em; margin-top: -20px; margin-left: 280px; align: left">Image from Zomer <em>et al.</em>, Stem Cells, 2013</div>
  </div>
* Current model cannot simulate *in vivo* tumor development - no space
* Next step - extend this to a spatial model
