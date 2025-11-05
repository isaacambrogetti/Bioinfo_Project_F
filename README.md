# Bioinfo_Project_F
Bioinformatics I project with Isaac, Morgane, Tom, Augustin


WE CANNOT ADD THE FILES HERE, THEY'RE TOO BIG.

make your folder accessible on your IBU student account so everyone can access it and download it from there.

- WT     /data/users/student10
- B4c3   /data/users/student12
- F24c1  /data/users/student10
- J44c1  /data/users/student07
- M56c1  /data/users/student35

Document that summirize the different candidates : 
https://docs.google.com/document/d/1hajHaNA2xPuqozHOgDlO1HliwpdW2S5aSGoMAu_H_tU/edit?usp=sharing


## Isaac followed this steps
How to filter from the complete VCF the variations that belong to your sample (change $11 to 10, 12 or 13), have quality > 10, are not mitochondrial, and are nonsense variations.
```
awk '($0 !~ /^#/ && $6 >= 10 && $8 ~ /ANN=[^|]*\|(stop_gained|frameshift_variant|disruptive_inframe|inframe_deletion|start_lost)\|/ && $1 !~ /Mito/ && $11 !~ /.\/.:.:.:.:.:./)' completeall_coding_max2.vcf > F24c1_filtered-strict.vcf
```
(Professor used the tools not a script)
> ⚠️  __Check if the mutation is homozygous, if not there’s a bug and you better ignore that entry.__

### Pipeline
Find gene, look for it in ensembl.org, read about it, open its UniProtKB page, check for interactions, open its BioGrid page and check for interactions there (Ctrl+F “MAP” -> look for MAPK interactions). Consider that the ones revealed by low throughput are the best, the others are not very precise.


| Chr | location | mutation | gene name | prot name | description |
|----------|----------|----------|----------|----------|----------|
| VI   | 5068   | start_lost   | YFL063W | - | Dubious open reading frame; unlikely to encode a functional protein, based on available experimental and comparative sequence data. No known interactions.|
| VIII   | 275671   | stop_gained   | YHR084W | STE12 | Transcription factor that is activated by a MAPK signaling cascade; activates genes involved in mating or pseudohyphal/invasive growth pathways; cooperates with Tec1p transcription factor to regulate genes specific for invasive growth. Proved to be interacting with DIG1: MAP kinase-responsive inhibitor of the Ste12p transcription factor; involved in the regulation of mating-specific genes the invasive growth pathway; related regulators Dig1p and Dig2p bind to Ste12p. |
| X   | 639997   | frameshift_variant   | YJR115W | - | Putative protein of unknown function; YJR115W has a paralog, ECM13, that arose from the whole genome duplication, which also has unknown function. |
| XIV   | 783539   | start_lost   | YNR077C | - | Protein of unknown function, abundance changes with carbon source |
