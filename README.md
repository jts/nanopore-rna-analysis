# Nanopore RNA Analysis

A collection of scripts for working with direct RNA/cDNA data.

## Transcript Quantification

`nanopore_transcript_abundance.py` estimates transcript abundance from reads mapped to a transcriptome. It uses an expectation-maximization approach like RSEM, Kallisto, salmon, etc to handle multi-mapping reads. The reads must be mapped to the transcript set using minimap2 with the `-p0` flag to retain all secondary mappings. Brief usage:

```
minimap2 -t 8 -x map-ont -p0 gencode.v27.transcripts.fa.gz direct_rna_reads.fastq > mappings.paf
python nanopore_transcript_abundance.py -i mappings.paf > abundance.tsv
```
