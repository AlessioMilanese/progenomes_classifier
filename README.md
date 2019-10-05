Progenome classifier
========
This tool classify genomes sequences (as well as metagenomic assembled genome) according to the specI taxonomy used in [Progenomes 2](http://progenomes.embl.de).

Pre-requisites
--------------
* Perl 5.24.0
* cdbtools
* Prodigal 2.6.3
* Python 2.7.12
* HMMER 3.1b2
* vsearch

If you have [conda](https://conda.io/docs/), you can install the dependencies and create an environment (after cloning the directory, see Installation):
```bash
cd progenomes_classifier/env
conda env create -f progenome-classifier.yaml
source activate progenome-classifier-ENV
```
Note: type `source deactivate` to deactivate an active environment.

Installation
--------------
```bash
git clone https://github.com/AlessioMilanese/progenomes_classifier.git
cd progenomes_classifier
python setup.py
```

Note: in the following examples we assume that the python script ```progenome-classifier``` is in the system path.


Simple example
--------------

Download the genome with id [AWWC00000000](https://www.ncbi.nlm.nih.gov/nuccore/AWWC00000000.1) that was assembled in the HMP project and annotated as *Jonquetella sp. BV3C21*
```bash
wget ftp://ftp.ncbi.nlm.nih.gov/sra/wgs_aux/AW/WC/AWWC01/AWWC01.1.fsa_nt.gz
gunzip AWWC01.1.fsa_nt.gz
```
(if it doesn't work, download JPFJ01.1.fsa_nt.gz from https://www.ncbi.nlm.nih.gov/Traces/wgs/AWWC01?display=contigs)

Find the taxonomy annotation with classify-genomes:
```bash
progenome-classifier AWWC01.1.fsa_nt
```

Which results in:
```
Extract genes...30.11 seconds
Map genes to specI database...176.53 seconds
Find assignemnt from genes...0.0 seconds
RESULT
fasta sequence: AWWC01.1.fsa_nt

kingdom: Bacteria
phylum: Synergistetes
class: Synergistia
order: Synergistales
family: Synergistaceae
genus: Jonquetella
species: Jonquetella anthropi [Jonquetella sp. BV3C21/Jonquetella anthropi]
specI: specI_v3_Cluster1951

Classification information
Number of detected genes: 40
Unique marker genes found in multiple copies [chimera?]: 0
Number of mapped genes: 40
Number of agreeing genes: 40
Percentage of agreeing genes: 100.0%

Single genes classification
COG0080_1	1111126.SAMN00829156.HMPREF1249_0389#COG0080#specI_v3_Cluster1951#1431462	100.0
COG0552_1	1111126.SAMN00829156.HMPREF1249_0400#COG0552#specI_v3_Cluster1951#2040739	100.0
COG0052_1	1111126.SAMN00829156.HMPREF1249_0177#COG0052#specI_v3_Cluster1951#733723	100.0
COG0172_1	1111126.SAMN00829156.HMPREF1249_1352#COG0172#specI_v3_Cluster1951#907725	100.0
COG0197_1	1111126.SAMN00829156.HMPREF1249_0105#COG0197#specI_v3_Cluster1951#560107	100.0
COG0522_1	1111126.SAMN00829156.HMPREF1249_1060#COG0522#specI_v3_Cluster1951#2385131	100.0
COG0215_1	1111126.SAMN00829156.HMPREF1249_1346#COG0215#specI_v3_Cluster1951#1169035	100.0
COG0092_1	1111126.SAMN00829156.HMPREF1249_0104#COG0092#specI_v3_Cluster1951#3424665	100.0
COG0124_1	1111126.SAMN00829156.HMPREF1249_1550#COG0124#specI_v3_Cluster1951#2735239	100.0
COG0098_1	1111126.SAMN00829156.HMPREF1249_0115#COG0098#specI_v3_Cluster1951#3337025	100.0
COG0093_1	1111126.SAMN00829156.HMPREF1249_0108#COG0093#specI_v3_Cluster1951#472563	100.0
COG0012_1	1111126.SAMN00829156.HMPREF1249_0599#COG0012#specI_v3_Cluster1951#994757	100.0
COG0099_1	1111126.SAMN00829156.HMPREF1249_0123#COG0099#specI_v3_Cluster1951#2909599	100.0
COG0090_1	1111126.SAMN00829156.HMPREF1249_0101#COG0090#specI_v3_Cluster1951#1866941	100.0
COG0091_1	1111126.SAMN00829156.HMPREF1249_0103#COG0091#specI_v3_Cluster1951#1256132	100.0
COG0049_1	1111126.SAMN00829156.HMPREF1249_1633#COG0049#specI_v3_Cluster1951#298269	100.0
COG0096_1	885272.SAMN02261412.JonanDRAFT_1081#COG0096#specI_v3_Cluster1951#1305752	100.0
COG0048_1	645512.SAMN00008831.GCWU000246_01347#COG0048#specI_v3_Cluster1951#346631	100.0
COG0097_1	1111126.SAMN00829156.HMPREF1249_0113#COG0097#specI_v3_Cluster1951#2125773	100.0
COG0016_1	1111126.SAMN00829156.HMPREF1249_0066#COG0016#specI_v3_Cluster1951#1954390	100.0
COG0541_1	1111126.SAMN00829156.HMPREF1249_0187#COG0541#specI_v3_Cluster1951#2212869	100.0
COG0201_1	1111126.SAMN00829156.HMPREF1249_0118#COG0201#specI_v3_Cluster1951#2822387	100.0
COG0088_1	1111126.SAMN00829156.HMPREF1249_0099#COG0088#specI_v3_Cluster1951#2559982	100.0
COG0184_1	1111126.SAMN00829156.HMPREF1249_0057#COG0184#specI_v3_Cluster1951#129414	100.0
COG0200_1	1111126.SAMN00829156.HMPREF1249_0117#COG0200#specI_v3_Cluster1951#1518621	100.0
COG0094_1	1111126.SAMN00829156.HMPREF1249_0110#COG0094#specI_v3_Cluster1951#2647658	100.0
COG0100_1	1111126.SAMN00829156.HMPREF1249_0124#COG0100#specI_v3_Cluster1951#3251551	100.0
COG0495_1	1111126.SAMN00829156.HMPREF1249_0208#COG0495#specI_v3_Cluster1951#3079577	100.0
COG0185_1	1111126.SAMN00829156.HMPREF1249_0102#COG0185#specI_v3_Cluster1951#2472558	100.0
COG0085_1	1111126.SAMN00829156.HMPREF1249_1630#COG0085#specI_v3_Cluster1951#2298076	100.0
COG0186_1	1111126.SAMN00829156.HMPREF1249_0107#COG0186#specI_v3_Cluster1951#1081795	100.0
COG0256_1	885272.SAMN02261412.JonanDRAFT_1079#COG0256#specI_v3_Cluster1951#4748	100.0
COG0087_1	1111126.SAMN00829156.HMPREF1249_0098#COG0087#specI_v3_Cluster1951#3166501	100.0
COG0525_1	1111126.SAMN00829156.HMPREF1249_0336#COG0525#specI_v3_Cluster1951#646915	100.0
COG0533_1	1111126.SAMN00829156.HMPREF1249_1262#COG0533#specI_v3_Cluster1951#2992754	100.0
COG0102_1	1111126.SAMN00829156.HMPREF1249_0252#COG0102#specI_v3_Cluster1951#1692863	100.0
COG0202_1	885272.SAMN02261412.JonanDRAFT_1068#COG0202#specI_v3_Cluster1951#1567250	100.0
COG0081_1	1111126.SAMN00829156.HMPREF1249_0390#COG0081#specI_v3_Cluster1951#212005	100.0
COG0018_1	1111126.SAMN00829156.HMPREF1249_1499#COG0018#specI_v3_Cluster1951#820760	100.0
COG0103_1	1111126.SAMN00829156.HMPREF1249_0251#COG0103#specI_v3_Cluster1951#1779538	100.0
```

Let's analyse the result:

the genome in the file `AWWC01.1.fsa_nt` is annotated as `Jonquetella anthropi`, which belongs to the specI `specI_v3_Cluster1951`.

The genome contains `40` marker genes (MGs) out of 40. The marker genes have the property to be present in single-copy in bacterial genomes, hence if the tool extract more than 40 MGs there might be problems with the genome that you are analysing (check `Unique marker genes found in multiple copies`). After that there is the information of the number of genes that were mapped to the specI database (`Number of mapped genes`) and the number of genes that support the consensus taxonomy `Number of agreeing genes` (as well as how much percentage of the found ones they represents, in this case `100%`).

Finally, there is a list with all the identified genes, the target gene in the specI database and the percentage identity.

Estimate correctness of the assignment
--------------

To test the classification accuracy we did a simulation (details below) where we removed some genomes from the database and we used them to test the progenome classifier. You can see the results for the precision of the classification (a proxy for the probability of correct assignment) in the following plot:
![alt text](https://github.com/AlessioMilanese/progenomes_classifier/blob/master/pics/precision.png)


Command options
--------------

The tool expect as input a fasta file:
```
progenome-classifier <fasta_file> [options]
```

The options are:
* **`-t`** number of threads (default 1)
* **`-v`** verbose level: 1=error, 2=warning, 3=message, 4+=debugging. Default is 3.
* **`-o`** save result to a file. Default is standard output.
* **`-m`** save the fasta sequence of the extracted marker genes.
* **`-M`** save the fasta sequence of the extracted marker genes and exit (do not map with vsearch).
* **`-s`** print the result in a single line. Useful if you want to analyse many genomes and cat all the taxonomies.
* **`-H`** print the result in html format
