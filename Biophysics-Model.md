# Biophysics-Model

Status: Done

# The Results for Molecular Dynamics Simulation

In order to characterize our split enzyme system (take TEV as an example) first, we have conducted the 10-ns OPLS-AA/L all-atom force field molecular dynamics through GROMACS, under the NPT equilibrium for a 300K, 1 bar, ion-neutral (balanced ions are Na+ and Cl-) environment. The following is the validation of our manipulation (Figure 1): 

![Figure. 1.svg](Biophysics-Model/Figure._1.svg)

**Figure 1: The validation of the molecular dynamics manipulation**

1. The energy minimization (EM) process before the manipulation.
2. The NVT equilibrium under the average of 300 K.
3. The NPT equilibrium under the average of 1 bar.
4. The density of the manipulation system

Following by the analyses of the trajectory results for TEV (Video 1), the Gibbs energy landscape (with principal component values to be gyration radius and RMSD) can be calculated and plotted (Figure 2).

[TEVp_Trajectory.mov](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/TEVp_Trajectory.mov)

**Video 1: The trajectory for the whole split enzyme system of TEV**

![Figure. 2.svg](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/Figure._2.svg)

**Figure 2: The Gibbs energy landscape of the TEV**

1. The gyration radius of the TEV.
2. The RMSD of the TEV.
3. the Gibbs energy landscape constructed through Rg and RMSD of the TEV.

As shown in the trajectory results, our system eventually converges to a compact and (local) energetic minimized state. We further investigate the flexibility of the TEV through its b-factor and electrostatic properties (Figure 3).

![image.gif](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/image.gif)

**Figure 3: Further investigation of the flexibility of the TEV**

1. The electrostatic properties of the TEV (red: negative; blue: positive).
2. The b-factor of the TEV, with the b-factor growing from lower (blue, rigid) to higher (white, flexible).

First of all, we can immediately extract the diffusion constant through the regression of the MSD (Figure 4), while the diffusion constant is an important physical parameters to be considered in our modeling for the split-enzyme system. The process to derive the relationship between the slop of MSD curve and the diffusion constant will be illustrated in the **measurements part**.

![MSD.svg](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/MSD.svg)

**Figure 4: The linear regression for the MSD value of the TEV to gain diffusion constant.**

Furthermore, by applying the same analyses logic to the nTEV and cTEV protein (10-ns OPLS-AA/L all-atom force field MD, Video 2 and Video 3), we have found some possible Phe sites for the clicking reaction which is vital to the linkage between the split enzyme and the aptamer. Eventually, we choose a pair of plausible Phe sites each on either nTEV or cTEV, due to the fact that they are away from the reaction core of the enzyme and lie in the flexible loop of the protein (Figure 5).

[nPPV.mov](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/nPPV.mov)

**Video 2: The trajectory analysis for nTEV**

[cTEVp.mov](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/cTEVp.mov)

**Video 3: The trajectory analysis for cTEV**

![image.gif](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/image%201.gif)

**Figure 5: The pair of Phe sites favorable for the clicking reaction**

1. The chosen Phe site on the nTEV protein.
2. The chosen Phe site on the cTEV protein.
3. The pair of chosen Phe sites on the TEV (with the b-factor the same as Figure. MD4).

Alternatively, we also perform the MD simulation for the PPV system as follows (Video 4 and Video 5), and eventually choose out the appropriate Phe sites for clicking reaction in Figure 6.

[nPPV copy.mov](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/nPPV_copy.mov)

**Video 4: The trajectory analysis for nPPV**

[cPPV copy.mov](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/cPPV_copy.mov)

**Video 5: The trajectory analysis for cPPV**

![PPV_Phe.png](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/PPV_Phe.png)

**Figure 6: The pair of Phe sites favorable for the clicking reaction in PPVp.**

# The Results of ODEs model for the biochemical system

We first construct the aptamer censoring system as follows (Figure 7), based on a few assumptions that:

1. There is no cooperativity between Apt. 1 and Apt. 2;
2. Compared to Aptamer, the target molecule is relative stable;
3. Ignore the inequilibrim effect given rise to the diffusion process;

We then construct the ODEs according to the basic chemical kinetics equations (Figure 8).

![image.gif](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/image%202.gif)

**Figure 7: Modeling of the aptamer censoring system.**

![image.gif](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/image%203.gif)

**Figure 8: ODEs of the aptamer censoring system.**

In Figure 9 (set the blue line as check-out line, the same for the following figures), we mimic such situation that both the aptamer A and aptamer B will die down quickly (with a relative high degradation rate compared with the target molecules), which we think will be the common cases for practical usage.

![FastCase.svg](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/FastCase.svg)

**Figure 9: Mimic of the fast-degradation case of the aptamer system.**

For the Figure 10, we decrease the initial ratio of both the aptamer A and aptamer B compared to the case above, in order to mimic the case when there only exist few targeting molecules in the sample.

![LowConcentartion.svg](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/LowConcentartion.svg)

**Figure 10: Mimic of the Low-Concentration Case of the aptamer system.**

In Figure 11, we assume that we have found better aptamer with higher affinity for the target molecules, which bring about both higher value of k1 and k2.

![SharpCase.svg](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/SharpCase.svg)

**Figure 11: Mimic of the Higher-Affinity aptamer case with sharp response.**

In Figure 12, the initial concentration of both aptamer A and B are identical, while aptamer A has a higher affinity over than aptamer B. As depicted in the figure, this asymmetry of the binding affinity can also bring about sharp peak of the checking out system.

![AsymmetricCase.svg](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/AsymmetricCase.svg)

**Figure 12: Asymmetric binding affinity between the aptamers can also introduce sharp response.**

Eventually, if the targeting molecules in the sample were at rather low concentration, and the amount of both aptamers were not enough, we would be confronted with the worst case for being unable to check out(Figure 13).

![WorstCase.svg](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/WorstCase.svg)

**Figure 13: Mimic of the worst-case of the aptamer system.**

Furthermore, we construct our down-stream amplification system under the guidance of basic Michaelis-Menten equation, while introducing the flipping: considering the enzyme can be flipping between either inactive and active states (Figure 14).

![image.gif](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/image%204.gif)

**Figure 14: The modeling and the ODEs of the amplification system.**

Considering the aptamer censoring system, we further assume that the whole amount of the enzyme will be constraint to exponential degradation:

![image.png](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/image.png)

And then we mimic for the amplification system as well:

If the degradation rate is high (Figure 15), the down-stream amplification can be inadequate. However, at a relative large parameter space volume, the amplification system can be robust and effective (Figure 16).

![Figure. 3.svg](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/Figure._3.svg)

**Figure 15: The fast-degradation case of the amplification system.**

1. The relative concentration of the product and the reagent in the fast-degradation case.
2. The different form of enzyme in the fast-degradation case.

![Figure. 4.svg](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/Figure._4.svg)

**Figure 16: The normal case of the amplification system.**

1. The relative concentration of the product and the reagent in the normal case.
2. The different form of enzyme in the fast-degradation case.

# Results of the PDEs model for the diffusion system

To describe the diffusion process in our biological system, we turn to the two-dimensional Fokker-Plank equation for characterizing our diffusion system. Again, we have made some plausible assumptions initially:

1. The oriented−dragging vector is only relate to the time t;
2. The diffusion constants for each biomolecules are not affected by time;

Based on the two-dimensional Fokker-Plank equation as follows:

![image.png](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/image%201.png)

With relative low dragging force v compared with the diffusion constant, the diffusion process can be rather normal (Video 6).

[Diffusion_case1.mov](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/Diffusion_case1.mov)

**Video 6: Low Oriented Dragging force diffusion**

Nevertheless, when the dragging force v is apparently higher than the diffusion rate, there can be turbulence (i.e. Multiple peaks) within the fixed volume (Video 7).

[Diffusion_case2.mov](Biophysics-Model%20b3deadac9aa542058c1c8d16e79632e8/Diffusion_case2.mov)

**Video 7: High Oriented Dragging force Diffusion**
