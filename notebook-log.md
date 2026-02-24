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
7. Within MAFFT, the command "mafft --localpair --maxiterate 1000 trnL_sequences.fasta > trnL_aligned.fasta" will be run. This was found at: https://manpages.debian.org/jessie/mafft/mafft-linsi.1.
- The assumptions of this method are that the sequences come from the same gene.
- This method is limited by speed - it takes a long time to run, and if the sequences do not match properly then inferring homology is limited.
- Descriptions of the command: L-INS-i: probably most accurate; recommended for <200 sequences; iterative refinement method incorporating local pairwise alignment information
