This page contains notes for people submitting genomes to GISAID or GenBank. 

[What it means when the genome submissions don't get accepted immediately](#when-covid-genome-submissions-do-not-get-accepted-immediately), 

how to fix the frameshift errors or when not to fix, 

and some interesting observations of where the real frameshift mutations tend on land the genome.


# When COVID genome submissions do not get accepted immediately

### GISAID 

GISAID only scans for [frameshifts](https://en.wikipedia.org/wiki/Frameshift_mutation) in the coding region, which can be caused by deletions or insertions of non-triplet of nucleotides. They return those sequences to submitters and direct quote from them "**your sequences with frameshift detection have not been rejected**, even if you want us to release the sequences as they are, you just have to let us know by email". 

The submitters can do one of the following:

1) Check the read alignment (bam file) surrounding the frameshift, if it is due to assembly error, fix it; if the assembly is supported by enough reads, re-submit as is.

2) If the frameshift is real, check ![this box](readme_image/gisaid_box.png) during submission. "The sequences will be released with a frameshift verification comment by the Submitter."

3) If the frameshift cannot be verified (such as no access to the read alignment bam file), resubmit as is but let GISAID know it wasn't verified. "Sequences are released with a non-verification comment from the Submitter."

I believe the "verfied frameshift" and "non-verified frameshift" are distinguished by ![this mark](readme_image/gisaid_mark.png) on GISAID... except I'm not sure which is which XD


### GenBank

GenBank will detect many [potential problems](https://github.com/ncbi/vadr/blob/master/documentation/alerts.md#top) the genomes may have, and if any of those errors land within the essential genes, they will not let the sequence in. There are a lot of [errors types](https://www.ncbi.nlm.nih.gov/genbank/sequencecheck/virus/) and some of the errors can be connected or originate from the same sequence problem, such as `CDS_HAS_FRAMESHIFT` can lead to `CDS_HAS_STOP_CODON` and `INDEFINITE_ANNOTATION_END` and `UNEXPECTED_LENGTH`. 

**The goal here is not to "fix" the genome until there is no more VADR errors.** The goal is to fix the assembly errors and leave whatever that is correctly-assembled and well-supported by reads as is, and convince GenBank staff that you have done the due diligence so they will accept the genomes. That being said, I have not succeeded in sending our rejected genomes in so this section to be completed TnT


# Types of frameshifts and how to fix them (or not to fix them)

Biohub only have **Illumina short read data** from metagenomic or ARTIC v3 libraries. Mis-assembly around INDELs is a lot more common for Nanopore data but I do not have enough experience to write about it. All our genomes were aligned with [minimap2 2.17](https://github.com/lh3/minimap2) and assembled with [iVar 1.2](https://github.com/andersen-lab/ivar). 

iVar does a fantastic job assembling genomes. However a fasta file with a linear genomic sequence has its limitations in faithfully representing the genomic sequence when the sample contains a mixture of more than 1 type of genomes. Naturally occurring intra-host variation or lab contamination both can lead to more than 1 type of genomes in the sample. If a position has A in some reads and C in some read

### Assembly errors (fix)

### Real frameshifts (do not fix)

### Random 1bp insertion (depending on the weather. I didn't.)

### Tough nuts. No good solution.

The genomic sequence in a fasta file is one linear sequence and things become tricky when there is more than one type of genomes, such as natural within host variation or . It allows some

# Some interesting observations
