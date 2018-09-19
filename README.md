# PRESM

PRESM stands for Personalized Reference Editor for Somatic Mutation discovery. In contrast to other reference genome editor software that generate a diploid reference genome which may distribute the reads to two site, impairing the soundness of the downstream statistical framework, PRESM provides two haploid reference genomes. The pipeline of PRESM involves three steps: First, germline mutations are discovered by another tool, e.g., GATK, and are used to make personalized references to call somatic mutations. Second, a reference genome composed of all personal variants (including both heterozygous and homozygous sites) is used as “decoy” to capture the heterozygous variants in reads. Third, PRESM changes the reads by replacing all heterozygous alleles with the corresponding reference alleles and maps the modified reads back to another personalized reference genome that contains only homozygous changes. The output of this step is a BAM file ready for any somatic mutation callers to use. We intend to offer long-term maintenance for PRESM and continue adding our new functions into it.

### Installation

PRESM is a batteries-included JAR executable; therefore no installation is needed. Please copy the executable presm.jar and run it using the standard command for java package:
java [–Xmx] –jar presm.jar

### Functions
* Processing variants files generated by GATK, Pindel or other variant call software, i.e., combining two variant files that are for SNPs and indels respectively; selecting homozygous variants or heterozygous variants; removing variants with duplicated coordinates.
* Generating the personalized reference genome according to the germline mutations provided by the users. 
* Generating the modified background database files according to personalized reference genomes, for example, the personalized dbSNP, db.Indel, and cosmic.vcf can be generated. (Several downstream somatic mutation callers require these files).
* Mapping the coordinates of somatic variants called by using personalized reference genome to the coordinates of universal
reference genome.
* Replacing the alternative alleles with reference bases according to the heterozygous variants provided by the users.

### Commands and options

All the functions are used as:
java [-Xmx] –jar /path/to/presm.jar <options>
  
  
**CombineVariants: Combine two variant call files according to the reference genome.**
```
> -F CombineVariants –R ref.fasta –variant1 input1.vcf –variant2 input2.vcf –O output.vcf
```
Parameters: 
* –R: input the reference genome file. 
* -variant1: input variant file 1 (in vcf foramt)
* -variant2: input variant file 2 (in vcf foramt)
* -O: output the combined variant call file in vcf format

**SelectGenotype: Select homozygous or heterozygous variants in the variant call file provided by the users.**
```
> -F SelectGenotype –genotype homo[heter] –variants input.vcf –O output.vcf
```
Parameters: 
* -genotype: Specify the genotype of the variants (homozygous/
heterozygous variants)
* -variants: input the variants in vcf format
* -O: output the specified genotype variants in vcf format


### Contacts
* Chen Cao, chen.cao@ucalgary.ca
* Quan Long, quan.long@ucalgary.ca

### Copyright License (MIT Open Source)
Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions: 

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
