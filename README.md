# Pipeline NGS
Pipeline code for my ngs project.

## Programs needed

- Demultiplexer
- LALIGN36
- BLAST
- MAFFT

### Installation

#### LALIGN36
```
git clone https://github.com/wrpearson/fasta36.git
cd fasta36/src
make -f ../make/Makefile.os_x86_64 all
```
Change ```Makefile.os_x86_64``` according to your operating system.

Then add the program to PATH, check the path in current directory using ```pwd```.

```
export PATH=$PATH:<PATH-TO-FASTA36-FOLDER>/bin
```

Confirm that it is working by typing ```lalign36 -h``` in your planned working directory.

## Pipeline

1. Demultiplex reads using - Demultiplexer
2. Extract ITS1 and ITS2 sequences from each read - LALIGN36 (fasta36 package)
3. Map each sequence to the nematode database - BLAST
4. Extract matches with %id higher than or equal to 80%
5. Align extracted matches - MAFFT
6. Variant calling
7. Align read to consensus and get variant calls
8. Calculate statistics and assign read.

Alternative pipeline (potentially more computionally sound)
1. Demultiplex reads using - Demultiplexer
3. Map each sequence to the ITS1 database and then ITS2 database - BLAST
4. Extract matches with %id higher than or equal to 80%
5. Align extracted matches - MAFFT
6. Align consensus match with read - LALIGN
7. Nanopolish
8. Variantcalling
9. Calculate statistics and combine results for ITS1 & ITS2

## About the strategy

### LALIGN36
After trying several pairwise aligners:
- Smith Waterman
- LALIGN

It was noted that LALIGN performed significantly better.

It was confirmed that LALIGN does also align the reverse compliment sequence by simply running the same sequence in both original and reverse compliment. In both cases the exact same identity was returned.
