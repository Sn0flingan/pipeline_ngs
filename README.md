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
