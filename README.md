# Botany563Project
### Introduction
Provides enough biological background for non-experts to understand the significance of the work
Provides the goal of the project clearly stated

This tree shows the phylogenetic relationships of several species from the Cupressaceae family: Calocedrus decurrens, Sequoia sempervirens, Hesperocyparis abramsiana, Hesperocyparis forbesii, Hesperocyparis macnabiana, Juniperus occidentalis, and Juniperus osteosperma. 

Several physiological functions of these species have been measured. Most importantly, this work focuses on the presence of transfusion tracheids, which are specialized cells that aid in effective movement of water within the xylem in gymnosperms. It is going to be assessed if variation in leaf morphology and tranfusion tracheid presence influence efficiency in handling drought stress. The phylogeny will be used to determine if trends in leaf hydraulic conductivity and other physiological traits are more environmentally or physiologically correlated. 

### Methods
provides data description: where it came from, size, characteristics
- Data was obtained from GenBank (sources will be listed below). Data accessions were from several different papers, each contributing different sequence markers. I compiled a list of 5 chloroplast and ribosomal sequences available for all species (matK, rps4-trnS, trnV intron, trnL-trnF, and trnK-matK) and (1) downloaded the FASTA files for each. 
- The number of base pairs per sequence varied:
  - matK: ~1524 bp
  - trnV intron: ~518 bp
  - rps4-trnS: ~768 bp
  - trnL-trnF: ~770 bp
  - trnK-matK: ~626 bp
2) I then aligned the data using MAFFT (Katoh, Kazutaka and Standley, Daron M. MAFFT Multiple Sequence Alignment Software Version 7: Improvements in Performance and Usability. Mol Biol Evol. 2013 Jan 16;30(4):772–780. doi: 10.1093/molbev/mst010.)
- MAFFT Description - MAFFT is a program used for multiple sequence alignment of nucleotides or amino acids (proteins).
- Strengths/Choices - Of the program overall: Can handle a lot of sequences, has many choices of algorithms from fast (FFT-NS1) to more accuracy based (L-INS-i, G-INS-i). Of chosen command: L-INS-i: probably most accurate; recommended for <200 sequences; iterative refinement method incorporating local pairwise alignment information.
- Weaknesses - This method is limited by speed - it takes a long time to run, and if the sequences do not match properly then inferring homology is limited.
- Assumptions - Sequences are homologous, and the inputted gap penalties/scoring matrices appropriately match the insertion/deletion process.

3) Beginning Trees were created using the R packages ape and phangorn. 

provides for every step in the pipeline: 1) name of the software, 2) reference, 3) short description of the method, 4) short description of strengths (why chosen?), 5) short description of weaknesses/limitations, 5) short description of the main assumptions of the method, 6) user choices (parameters that you had to choose and how)

### Results
provides estimated tree with some discussion on the original biological question from the introduction

provides measures of support to the tree

### Sources
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
