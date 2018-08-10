# Pipeline NGS
Pipeline code for my ngs project.

## Programs needed

- Demultiplexer
- LALIGN36
- BLAST
- MAFFT

## Pipeline

1. Demultiplex reads using - Demultiplexer
2. Extract ITS1 and ITS2 sequences from each read - LALIGN36 (fasta36 package)
3. Map each sequence to the nematode database - BLAST
4. Extract matches with %id higher than or equal to 80%
5. Align extracted matches - MAFFT
6. Variant calling
7. Align read to consensus and get variant calls
8. Calculate statistics and assign read.
