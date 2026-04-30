# Botany563Project
### Abstract
This phylogeny summarizes the relationships of seven conifer species in the Cupressaceae family that have been analyzed for physiological traits of hydraulic conductivity and transfusion tracheids. Starting sequences of 5 chloroplast genes (matK, trnV intron, rps4-trnS, trnL-trnF, trnK-matK) were obtained from Genbank and aligned in the software MAFFT. The aligned sequences were then used to create separate gene trees in the following softwares: MrBayes, IQTree, and ape/phangorn in R studio. All gene trees were then coalesced using Astral, which did not work super effectively due to a low number of genes present. Ultimately, the most appropriate gene tree due to maximum bootstrap support, genera clustering together properly, and coordinated physiological responses was from the gene matK in MrBayes. 

### Introduction
This tree shows the phylogenetic relationships of several species from the Cupressaceae family: Calocedrus decurrens, Sequoia sempervirens, Hesperocyparis abramsiana, Hesperocyparis forbesii, Hesperocyparis macnabiana, Juniperus occidentalis, and Juniperus osteosperma. 

Several physiological functions of these species have been measured. Most importantly, this work focuses on the presence of transfusion tracheids, which are specialized cells that aid in effective movement of water within the leaf xylem in gymnosperms. It is going to be assessed if variation in leaf morphology and tranfusion tracheid presence influence efficiency in handling drought stress. The phylogeny will be used to determine if trends in leaf hydraulic conductivity and other physiological traits are more environmentally or phylogenetically correlated. 

### Methods
- Data was obtained from GenBank (sources listed below). Data accessions were from several different papers, each contributing different sequence markers. I compiled a list of 5 chloroplast marker sequences available for all species (matK, rps4-trnS, trnV intron, trnL-trnF, and trnK-matK) for all 7 species and (1) downloaded the FASTA files for each. 
- The number of base pairs per sequence varied:
  - matK: ~1524 bp
  - trnV intron: ~518 bp
  - rps4-trnS: ~768 bp
  - trnL-trnF: ~770 bp
  - trnK-matK: ~626 bp
2) I then aligned the data using MAFFT. 
- Description - MAFFT is a program used for multiple sequence alignment of nucleotides or amino acids (proteins).
- Strengths/Choices - Of the program overall: Can handle a lot of sequences, has many choices of algorithms from fast (FFT-NS1) to more accuracy based (L-INS-i, G-INS-i). Of chosen command: L-INS-i: probably most accurate; recommended for <200 sequences; iterative refinement method incorporating local pairwise alignment information.
- Weaknesses - This method is limited by speed - it takes a long time to run, and if the sequences do not match properly then inferring homology is limited.
- Assumptions - Sequences are homologous, and the inputted gap penalties/scoring matrices appropriately match the insertion/deletion process.

3) Beginning NJ Trees were created using the R packages ape and phangorn.
   
Software - Ape 
- Description - An R package used for a variety of functions to do basic phylogenetic tree manipulation and visualization, but namely it can be used to estimate distance-based trees. 
- Strengths - Easy to use in R/R studio. Supports a variety of tree formats and includes distance based tree building such as Neighbor-joining. It can also integrate with other R packages easily. 
- Weaknesses - It has limited phylogenetic inference methods and isn't as optimized for large datasets compared to phangorn.
- Assumptions - Assumes that the tree manipulation has the correct topology input.
- User choices - NA

Software - phangorn 
- Description - An R package used for a variety of functions such as phylogenetic reconstruction using maximum likelihood and parsimony methodologies. 
- Strengths - Easy to use in R, supports many substitution models (GTR, HKY, etc.), can run bootstrap support, and parsimony analyses.
- Weaknesses - The run time is slow.
- Assumptions - That sequences follow a specified substitution model, sites evolve independently, and that your initial alignment is correct. 

4) I then use RAxML and IQTree to create 5 separate trees for each set of sequences using maximum likelihood methods.
Software - RAxML
- Description -  Software used for maximum likelihood methods, and can be run with protein or amino acid sequences.
- Strengths - Good for large datasets, is accurate and produces robust trees, and implements bootstrap values.
- Weaknesses - Computationally intensive and does not guarantee the correct local optima is chosen.
- Assumptions - The correct model of evolution is specified, all sites evolve independently, each branch evolves independently, and that sequences are homologous.
- User choices - Substitution model, partitioning scheme, bootstrap settings, number of ML trees created.

Software - IQTree
- Description -  Software used for maximum likelihood methods, and can be run with protein or amino acid sequences.
- Strengths - Good for large datasets, is accurate and produces robust trees, implements bootstrap values, and incorporates model selection through ModelFinder.
- Weaknesses - Computationally intensive and does not guarantee the correct local optima is chosen.
- Assumptions - The correct model of evolution is specified, all sites evolve independently, each branch evolves independently, and that sequences are homologous.
- User choices - Substitution model, partitioning scheme, bootstrap settings, number of ML trees created.

5) I then used MrBayes to estimate Bayesian inferences of posterior distributions using MCMC methods.
- Description - Software used for Bayesian inferences using MCMC methods to estimate posterior distributions.
- Strengths - Provides posterior probabilities, supports a lot of models (GTR, HKY), can combine molecular and morphological data.
- Weaknesses - MCMC can be slow.
- Assumptions - Data is from homologous genes.
- User choices - How many times the program runs.

6) I then used Astral to combine the 5 gene trees.
-  Software - Astral
- Description - Coalescent based method for inferring species trees from multiple gene trees. 
- Strengths - Fast, scalable, and statistically consistent.
- Weaknesses - Sensitive to gene tree error and prior mistakes in the pipeline.
- Assumptions - Gene trees are correctly built and that there is no recombination within loci. 
- User Choices - Rooting, gene tree inputs, and filtering of present genes. 

### Results
All results of IQTree and Astral can be found at this link: https://docs.google.com/document/d/1Pbk99NNbKAXw8DGiwlLSt01qsIn_fBv5ltRwBESizBA/edit?tab=t.0.

The most appropriate final tree is the matK MrBayes Tree. There are high levels of nodal support by bootstrapping, with 2 clades at 100 (JUOC - Juniperus occidentalis, JUOS - Juniperus osteosperma; and HEMA - Hesperocyparis abramsiana, HEFO - Hesperocyparis forbesii, HEMA - Hesperocyparis macnabiana) and 2 splits in topology also at 100. There is one outgroup at the root between SESE - Sequioa sempervirens and CADE - Calocedrus decurrens. This is what I would expect to see, as the different genera are clustering properly together and the two outgroups are accurately displayed. 

### Discussion
The conclusion of my finding show that the one of physiological traits I measured is coordinated phylogenetically, but not both. Each clade has species with similar amounts of transfusion tracheids, but varying levels of hydraulic conductivities. This shows that the cellular level traits within the leaf are likely structural, and have a genetic component inducing a similar pattern in the leaf. Whereas, the hydraulic conductivity, the amount of water that can move through the stem, seems to be more environmentally respondent. This makes sense, as the longterm effects of drought insight the development of thicker cell walls in the xylem. So, within similar genera or sister species, the responses of how much water can move depends on how much continuous water they are supplied. Plants with high levels of water will have less resistant xylem to hydraulic collapse, as they are not used to drying out, so they'll have lower conductivity. This pattern could even be evident interspecifically. 

I found the most accurate gene level tree from MrBayes with bootstrap support. A major limitation of my study was the low level of species and genes available. This was evident when I ran Astral, as there was effectively not enough data for the software to run properly. In the future, I will be running Beast to see if I can create an accurate coalescent based tree. I also will be continuing to search Genbank for more available genes, optimally ribosomal genes to diversify from only chloroplast genes currently. 

### Sources
- MAFFT: Katoh, Kazutaka and Standley, Daron M. MAFFT Multiple Sequence Alignment Software Version 7: Improvements in Performance and Usability. Mol Biol Evol. 2013 Jan 16;30(4):772–780. doi: 10.1093/molbev/mst010.
- APE: https://emmanuelparadis.github.io/
- Phangorn: https://cran.r-project.org/web/packages/phangorn/index.html
- RAxML: Kozlov, A.M, Darriba, D., Flouri, T., Morel, B., Stamatakis, A. RAxML-NG: a fast, scalable and user-friendly tool for maximum likelihood phylogenetic inference, Bioinformatics, Volume 35, Issue 21, November 2019, Pages 4453–4455, https://doi.org/10.1093/bioinformatics/btz305.
- IQTree: Nguyen, L-T., Schmidt, H. A., von Haeseler, A., Minh, B. Q. IQ-TREE: A Fast and Effective Stochastic Algorithm for Estimating Maximum-Likelihood Phylogenies, Molecular Biology and Evolution, Volume 32, Issue 1, January 2015, Pages 268–274, https://doi.org/10.1093/molbev/msu300
- MrBayes: Ronquist, F., Teslenko, M., van der Mark, P., Ayres, D. L., Darling, A., Höhna, S., Larget, B., Liu, L., Suchard, M. A., Huelsenbeck, J. P. MrBayes 3.2: Efficient Bayesian Phylogenetic Inference and Model Choice Across a Large Model Space, Systematic Biology, Volume 61, Issue 3, May 2012, Pages 539–542, https://doi.org/10.1093/sysbio/sys029
- Astral: https://github.com/smirarab/ASTRAL/blob/master/astral-tutorial-template.md#running-on-the-sample-mammalian-dataset.

Calocedrus decurrens:
- matK: Cheng, Y., Nicolson, R.G., Tripp,K. and Chaw, S.M. Phylogeny of taxaceae and cephalotaxaceae genera inferred from chloroplast matK gene and nuclear rDNA ITS region. Mol. Phylogenet. Evol. 14 (3), 353-365 (2000).
- trnV intron: Mao, K., Hao, G., Liu, J., Adams, R.P. and Milne, R.I. Diversification and biogeography of Juniperus (Cupressaceae): variable diversification rates and multiple intercontinental dispersals. New Phytol. 188 (1), 254-272 (2010). 
- rps4-trnS: Mao,K., Hao, G., Liu,J., Adams,R.P. and Milne,R.I. Diversification and biogeography of Juniperus (Cupressaceae): variable diversification rates and multiple intercontinental dispersals. New Phytol. 188 (1), 254-272 (2010).
- trnL-trnF: Mao,K. and Liu,J. Diversification and biogeography of Juniperus (Cupressaceae): a Madrean-Tethyan tale? Unpublished. 
- trnK-matK: Crisp,M., Cook,L., Bowman,D., Cosgrove,M., Isagi,Y. and Sakaguchi,S. Turnover of southern cypresses in the post-Gondwanan world: extinction, transoceanic dispersal, adaptation and rediversification. Unpublished.

Sequoia sempervirens
- matK: Kusumi,J., Tsumura,Y., Yoshimaru,H. and Tachida,H. Phylogenetic relationships in Taxodiaceae and Cupressaceae sensu stricto based on matK gene, chlL gene, trnL-trnF IGS region, and trnL intron sequences. Am. J. Bot. 87 (10), 1480-1488 (2000)
- trnV intron: Guo,Y.-Y., Xiang,Q.-P. and Farjon,A. Phylogenetic relationships of Xanthocyparis (Cupressaceae) and its relatives inferred from chloroplast trnV intron and petG-trnP intergenic spacer sequences. Unpublished.
- rps4-trnS: Mao,K., Hao,G., Liu,J., Adams,R.P. and Milne,R.I. Diversification and biogeography of Juniperus (Cupressaceae): variable diversification rates and multiple intercontinental dispersals. New Phytol. 188 (1), 254-272 (2010). 
- trnL-trnF: Sekiewicz,K., Dering,M., Romo,A., BouDagher-Kharrat,M., Boratynska,K., Ok,T. and Boratynski,A. Phylogenetic and biogeographic insights into long-lived Mediterranean Cupressus taxa with a schizo-endemic distribution and tertiary origin. Unpublished.
- trnK-matK: Crisp,M., Cook,L., Bowman,D., Cosgrove,M., Isagi,Y. and Sakaguchi,S. Turnover of southern cypresses in the post-Gondwanan world: extinction, transoceanic dispersal, adaptation and rediversification. Unpublished.

Hesperocyparis abramsiana
- matK: Mao,K., Hao,G., Liu,J., Adams,R.P. and Milne,R.I. Diversification and biogeography of Juniperus (Cupressaceae): variable diversification rates and multiple intercontinental dispersals. New Phytol. 188 (1), 254-272 (2010). 
- trnV intron:  Mao,K., Hao,G., Liu,J., Adams,R.P. and Milne,R.I. Diversification and biogeography of Juniperus (Cupressaceae): variable diversification rates and multiple intercontinental dispersals. New Phytol. 188 (1), 254-272 (2010). 
- rps4-trnS: Mao,K., Hao,G., Liu,J., Adams,R.P. and Milne,R.I. Diversification and biogeography of Juniperus (Cupressaceae): variable diversification rates and multiple intercontinental dispersals. New Phytol. 188 (1), 254-272 (2010). 
- trnL-trnF: Mao,K. and Liu,J. Diversification and biogeography of Juniperus (Cupressaceae): a Madrean-Tethyan tale? Unpublished. 
- trnK-matK: Little,D.P. Evolution and Circumscription of the True Cypresses (Cupressaceae: Cupressus). Syst. Bot. 31 (3), 461-480 (2006). 

Hesperocyparis forbesii
- matK: Mao,K., Hao,G., Liu,J., Adams,R.P. and Milne,R.I. Diversification and biogeography of Juniperus (Cupressaceae): variable diversification rates and multiple intercontinental dispersals. New Phytol. 188 (1), 254-272 (2010). 
- trnV intron: Mao,K., Hao,G., Liu,J., Adams,R.P. and Milne,R.I. Diversification and biogeography of Juniperus (Cupressaceae): variable diversification rates and multiple intercontinental dispersals. New Phytol. 188 (1), 254-272 (2010). 
- rps4-trnS: Mao,K., Hao,G., Liu,J., Adams,R.P. and Milne,R.I. Diversification and biogeography of Juniperus (Cupressaceae): variable diversification rates and multiple intercontinental dispersals. New Phytol. 188 (1), 254-272 (2010). 
- trnL-trnF: Mao,K. and Liu,J. Diversification and biogeography of Juniperus (Cupressaceae): a Madrean-Tethyan tale? Unpublished. 
- trnK-matK: Little,D.P. Evolution and Circumscription of the True Cypresses (Cupressaceae: Cupressus). Syst. Bot. 31 (3), 461-480 (2006). 

Hesperocyparis macnabiana
- matK: Little,D.P. Documentation of Hybridization Between Californian Cypresses: Cupressus macnabiana sargentii. Syst. Bot. 29 (4), 825-833 (2004).
- trnV intron: Mao,K., Hao,G., Liu,J., Adams,R.P. and Milne,R.I. Diversification and biogeography of Juniperus (Cupressaceae): variable diversification rates and multiple intercontinental dispersals. New Phytol. 188 (1), 254-272 (2010). 
- rps4-trnS: Mao,K., Hao,G., Liu,J., Adams,R.P. and Milne,R.I. Diversification and biogeography of Juniperus (Cupressaceae): variable diversification rates and multiple intercontinental dispersals. New Phytol. 188 (1), 254-272 (2010). 
- trnL-trnF: Mao,K. and Liu,J. Diversification and biogeography of Juniperus (Cupressaceae): a Madrean-Tethyan tale? Unpublished.
- trnK-matK: Little,D.P., Schwarzbach,A.E., Adams,R.P. and Hsieh,C.F. The circumscription and phylogenetic relationships of Callitropsis and the newly described genus Xanthocyparis (Cupressaceae). Am. J. Bot. 91 (11), 1872-1881 (2004).
  
Juniperus occidentalis
- matK: Mao,K., Hao,G., Liu,J., Adams,R.P. and Milne,R.I. Diversification and biogeography of Juniperus (Cupressaceae): variable diversification rates and multiple intercontinental dispersals. New Phytol. 188 (1), 254-272 (2010). 
- trnV intron: Mao,K., Hao,G., Liu,J., Adams,R.P. and Milne,R.I. Diversification and biogeography of Juniperus (Cupressaceae): variable diversification rates and multiple intercontinental dispersals. New Phytol. 188 (1), 254-272 (2010). 
- rps4-trnS: Mao,K., Hao,G., Liu,J., Adams,R.P. and Milne,R.I. Diversification and biogeography of Juniperus (Cupressaceae): variable diversification rates and multiple intercontinental dispersals. New Phytol. 188 (1), 254-272 (2010). 
- trnL-trnF: Mao,K. and Liu,J. Diversification and biogeography of Juniperus (Cupressaceae): a Madrean-Tethyan tale? Unpublished.
- trnK-matK: Little,D.P. Evolution and Circumscription of the True Cypresses (Cupressaceae: Cupressus). Syst. Bot. 31 (3), 461-480 (2006). 

Juniperus osteoperma
- matK: Mao,K., Hao,G., Liu,J., Adams,R.P. and Milne,R.I. Diversification and biogeography of Juniperus (Cupressaceae): variable diversification rates and multiple intercontinental dispersals. New Phytol. 188 (1), 254-272 (2010). 
- trnV intron:  Mao,K., Hao,G., Liu,J., Adams,R.P. and Milne,R.I. Diversification and biogeography of Juniperus (Cupressaceae): variable diversification rates and multiple intercontinental dispersals. New Phytol. 188 (1), 254-272 (2010). 
- rps4-trnS: Mao,K., Hao,G., Liu,J., Adams,R.P. and Milne,R.I. Diversification and biogeography of Juniperus (Cupressaceae): variable diversification rates and multiple intercontinental dispersals. New Phytol. 188 (1), 254-272 (2010).
- trnL-trnF: Mao,K. and Liu,J. Diversification and biogeography of Juniperus (Cupressaceae): a Madrean-Tethyan tale? Unpublished.
- trnK-matK: Little,D.P. Evolution and Circumscription of the True Cypresses (Cupressaceae: Cupressus). Syst. Bot. 31 (3), 461-480 (2006). 
