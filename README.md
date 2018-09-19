# PRESM

PRESM stands for Personalized Reference Editor for Somatic Mutation discovery. In contrast to other reference genome editor software that generate a diploid reference genome which may distribute the reads to two site, impairing the soundness of the downstream statistical framework, PRESM provides two haploid reference genomes. The pipeline of PRESM involves three steps: First, germline mutations are discovered by another tool, e.g., GATK, and are used to make personalized references to call somatic mutations. Second, a reference genome composed of all personal variants (including both heterozygous and homozygous sites) is used as “decoy” to capture the heterozygous variants in reads. Third, PRESM changes the reads by replacing all heterozygous alleles with the corresponding reference alleles and maps the modified reads back to another personalized reference genome that contains only homozygous changes. The output of this step is a BAM file ready for any somatic mutation callers to use. We intend to offer long-term maintenance for PRESM and continue adding our new functions into it.

### Installation

PRESM is a batteries-included JAR executable; therefore no installation is needed. Please copy the executable presm.jar and run it using the standard command for java package:\n
java [–Xmx] –jar presm.jar

### Usage

**Eigen-decomposition for Symmetric Matrices** 
```
> ocma eigen disk/memory n A E Q
```
Parameters: 
* disk/memory: Specifies whether using disk or memory. 
* n (input): The row number and column number of matrix A.
* A (input): The filename of the file that stores matrix A. The size of the file should be n*n*sizeof(float).
* E (output): The filename of the file that stores the eigenvalues of matrix A. The file size is n*sizeof(float).
* Q (output): The filename of the file that stores the eigenvectors of matrix A. The file size is n*n*sizeof(float).

**Singular Value Decomposition**
```
> ocma singular disk/memory m n A S U V
```
Parameters: 
* disk/memory: Specifies whether using disk or memory. 
* m (input): The row number of matrix A.
* n (input): The column number of matrix A.
* A (input): The filename of the file that stores matrix A. The size of the file should be m*n*sizeof(float).
* S (output): The filename of the file that stores the singular values of matrix A. The size of the file is min(m,n)*sizeof(float).
* U (output): The filename of the file that stores the left-singular vectors of matrix A. The size of the file is m*min(m,n)*sizeof(float).
* V (output): The filename of the file that stores the right-singular vectors of matrix A. The size of the file is n*min(m,n)*sizeof(float).

**Part Singular Value Decomposition**
```
> ocma singularpart disk/memory m n k A S U V
```
Parameters: 
* disk/memory: Specifies whether using disk or memory. 
* m (input): The row number of matrix A.
* n (input): The column number of matrix A.
* k (input): The number of singular values. k <= min(m,n) is required. 
* A (input): The filename of the file that stores matrix A. The size of the file should be m*n*sizeof(float).
* S (output): The filename of the file that stores the singular values of matrix A. The size of the file is k*sizeof(float).
* U (output): The filename of the file that stores the left-singular vectors of matrix A. The size of the file is m*k*sizeof(float).
* V (output): The filename of the file that stores the right-singular vectors of matrix A. The size of the file is n*k*sizeof(float).

**Matrix Format Conversion**
```
> ocma format txt2bin/bin2txt m n A B
```
Parameters: 
* txt2bin/bin2txt: Specifies to convert text to binary format or in reverse. 
* m (input): The row number of matrix A.
* n (input): The column number of matrix A.
* A (input): The filename of the file that stores matrix A in text/binary format.
* B (output): The filename of the file that stores the matrix in binary/text format.

Note: 
For all file names, the file path must be specified if the file in question is not present in the current working directory.

### Contacts
* Chen Cao, chen.cao@ucalgary.ca
* Quan Long, quan.long@ucalgary.ca

### Copyright License (MIT Open Source)
Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions: 

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
