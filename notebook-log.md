I am going to work with several species from the Cupressaceae family: Calocedrus decurrens, Sequoia sempervirens, Hesperocyparis abramsiana, Hesperocyparis forbesii, Hesperocyparis macnabiana, Juniperus occidentalis, and Juniperus osteosperma. Available sequences of chloroplast DNA (rbs4, matk, trn V intron, trn L–trn F, trn K–mat K) will be obtained from GenBank. 
---
# Notebook reproducible script for Botany 563

### Installation
1. Install Anaconda from Anaconda.org by choosing the `Windows 64-Bit Graphical Installer` file from the list here: https://www.anaconda.com/download/success

2. We double-clicked on the file and followed the installation steps

3. We get into the Anaconda page and open the Anaconda powershell for windows

4. Check up at this point:
```shell
$ where conda
```
5. Install MAFFT from https://mafft.cbrc.jp/alignment/software/windows_without_cygwin.html following the steps for Windows 64
6. Then checked by running:
```shell
   $ where MAFFT
```

### Alignment
7. Within MAFFT, the command "mafft --localpair --maxiterate 1000 sequences.fasta > aligned.fasta" will be run. This was found at: https://manpages.debian.org/jessie/mafft/mafft-linsi.1.
Software - MAFFT
Description- MAFFT is a program used for multiple sequence alignment of nucleotides or amino acids (proteins). 
Strengths - Of the program overall: Can handle a lot of sequences, has many choices of algorithms from fast (FFT-NS1) to more accuracy based (L-INS-i, G-INS-i). Of chosen command: L-INS-i: probably most accurate; recommended for <200 sequences; iterative refinement method incorporating local pairwise alignment information.
Weaknesses - This method is limited by speed - it takes a long time to run, and if the sequences do not match properly then inferring homology is limited.
Assumptions - Sequences are homologous, and the inputted gap penalties/scoring matrices appropriately match the insertion/deletion process.

8. MAFFT was opened manually. The windows key was pressed to start a search, and then I typed cmd and pressed enter. I then changed the directory to my computer by running cd C:\Users\andre\Downloads. Then, MAFFT was run by mafft sequences.fasta > aligned.fasta. The alignment was then created as FASTA_output.

### Beginning Trees 
9. Following the methods from the "Distance/Parsiomny methods (Part 3: computer lab)" from the Botany 563 Course website, I created a basic NJ tree from the R packages ape and phangorn by substituting out the sample dataset for my own. 
Software - Ape 
Description - An R package used for a variety of functions to do basic phylogenetic tree manipulation and visualization, but namely it can be used to estimate distance-based trees. 
Strengths - Easy to use in R/R studio. Supports a variety of tree formats and includes distance based tree building such as Neighbor-joining. It can also integrate with other R packages easily. 
Weaknesses - It has limited phylogenetic inference methods and isn't as optimized for large datasets compared to phangorn.
Assumptions - Assumes that the tree manipulation has the correct topology input.
User choices - NA

Software - phangorn 
Description - An R package used for a variety of functions such as phylogenetic reconstruction using maximum likelihood and parsimony methodologies. 
Strengths - Easy to use in R, supports many substitution models (GTR, HKY, etc.), can run bootstrap support, and parsimony analyses.
Weaknesses - The run time is slow.
Assumptions - That sequences follow a specified substitution model, sites evolve independently, and that your initial alignment is correct. 

Steps copied below:
1) Installing necessary packages:

install.packages("adegenet", dep=TRUE)
install.packages("phangorn", dep=TRUE)

2) Loading the packages

library(ape)
library(adegenet)
library(phangorn)

3) Loading the sample data

dna <- fasta2DNAbin(file="http://adegenet.r-forge.r-project.org/files/usflu.fasta")

4) Computing the genetic distances. They choose a Tamura and Nei 1993 model which allows for different rates of transitions and transversions, heterogeneous base frequencies, and between-site variation of the substitution rate.

D <- dist.dna(dna, model="TN93")

5) Get the NJ tree

tre <- nj(D)

6) Before plotting, we can use the ladderize function which reorganizes the internal structure of the tree to get the ladderized effect when plotted

tre <- ladderize(tre)

7) We can plot the tree

plot(tre, cex=.6)
title("A simple NJ tree")

And then:
1) Installing necessary packages (if you have not installed them for the distance section above)

install.packages("adegenet", dep=TRUE)
install.packages("phangorn", dep=TRUE)

2) Loading

library(ape)
library(adegenet)
library(phangorn)

3) Loading the sample data and convert to phangorn object:
(These were the 'toy' data set names - I renamed my files to the same for convenience in coding). 
dna <- fasta2DNAbin(file="http://adegenet.r-forge.r-project.org/files/usflu.fasta")
dna2 <- as.phyDat(dna)

4) We need a starting tree for the search on tree space and compute the parsimony score of this tree

tre.ini <- nj(dist.dna(dna,model="raw"))
parsimony(tre.ini, dna2)

5) Search for the tree with maximum parsimony:

> tre.pars <- optim.parsimony(tre.ini, dna2)

6) Plot tree:

plot(tre.pars, cex=0.6)

### RAxML
Software - RAxML
Description -  Software used for maximum likelihood methods, and can be run with protein or amino acid sequences.
Strengths - Good for large datasets, is accurate and produces robust trees, and implements bootstrap values.
Weaknesses - Computationally intensive and does not guarantee the correct local optima is chosen.
Assumptions - The correct model of evolution is specified, all sites evolve independently, each branch evolves independently, and that sequences are homologous.
User choices - Substitution model, partitioning scheme, bootstrap settings, number of ML trees created.

I click on Download Download 64-bit Linux binary and I download C:\Users\Rose\Downloads\raxml-ng_v2.0.0_linux_x86_64.zip. 

cd C:\Users\Rose\Downloads\raxml-ng_v2.0.0_linux_x86_64.zip. 
ls ## check the raxml-ng executable is there
cp raxml-ng 

First, we will check the alignment:
raxml-ng --check --msa primatesAA-aligned-muscle.fasta --model LG+G8+F

And then we find the ML tree:
raxml-ng --msa primatesAA-aligned-muscle.fasta --model LG+G8+F

RAxML produces the following output files:
Best ML tree saved to: primatesAA-aligned-muscle.fasta.raxml.bestTree
All ML trees saved to: primatesAA-aligned-muscle.fasta.raxml.mlTrees
Optimized model saved to: primatesAA-aligned-muscle.fasta.raxml.bestModel
Execution log saved to: primatesAA-aligned-muscle.fasta.raxml.log

We can do a quick and dirty plot in R:
library(ape)
tre = read.tree(file="primatesAA-aligned-muscle.fasta.raxml.bestTree")
plot(tre)

Non-parametric bootstrapping:
We use the flag --all to run both ML and bootstrap:
raxml-ng --all --msa primatesAA-aligned-muscle.fasta --model LG+G8+F --bs-trees 10 --prefix primatesAA-aligned-muscle-raxml-boostrap
We are only doing 10 bootstrap replicates for the sake of time, but we should always try to do at least 100. We need to choose a new prefix because it doesn’t let us overwrite the previous raxml output files.

The output file we are interested in is:
Best ML tree with Felsenstein bootstrap (FBP) support values saved to: primatesAA-aligned-muscle-raxml-boostrap.raxml.support

We can do a quick and dirty plot in R:
library(ape)
tre = read.tree(file="primatesAA-aligned-muscle-raxml-boostrap.raxml.support")
plot(tre)
nodelabels(tre$node.label)

First, we note that the tree does not seem to be rooted correctly.

very important

Maximum likelihood methods are uncapable of inferring the place of the root. We always have to root the estimated tree afterwards with an outgroup.

library(ape)
tre = read.tree(file="primatesAA-aligned-muscle-raxml-boostrap.raxml.support")
plot(tre)
nodelabels()
rtre = root(tre, node=33, resolve.root=TRUE)

### MrBayes
Description - Software used for Bayesian inferences using MCMC methods to estimate posterior distributions. Strengths - Provides posterior probabilities, supports a lot of models (GTR, HKY), can combine molecular and morphological data. Weaknesses - MCMC can be slow. Assumptions - Data is from homologous genes. User choices - How many times the program runs.

I downloaded MrBayes from https://nbisweden.github.io/MrBayes/. I chose the option for Windows: MrBayes-3.2.7-WIN.zip. 

I then created a mrbayes block in a text file named mbblock.txt. I then added mcmc;sumt; at the end of the file. 

I then ran this block: 
begin mrbayes;
 set autoclose=yes;
 prset brlenspr=unconstrained:exp(10.0);
 prset shapepr=exp(1.0);
 prset tratiopr=beta(1.0,1.0);
 prset statefreqpr=dirichlet(1.0,1.0,1.0,1.0);
 lset nst=2 rates=gamma ngammacat=4;
 mcmcp ngen=10000 samplefreq=10 printfreq=100 nruns=1 nchains=3 savebrlens=yes;
 outgroup HEFO;
 mcmc;
 sumt;
end;

After, I added the MrBayes Block to my nexus file. 
cat algaemb.nex mbblock.txt > algaemb-mb.nex

and ran MrBayes: mb algaemb-mb.nex
