    PRESM stands for Personalized Reference Editor for Somatic Mutation discovery. In contrast to other reference genome editor software
    
that generate a diploid reference genome which may distribute the reads to two site, impairing the soundness of the downstream statistical 
framework, PRESM provides two haploid reference genomes. The pipeline of PRESM involves three steps: First, germline mutations are 
discovered by another tool, e.g., GATK, and are used to make personalized references to call somatic mutations. Second, a reference genome 
composed of all personal variants (including both heterozygous and homozygous sites) is used as “decoy” to capture the heterozygous 
variants in reads. Third, PRESM changes the reads by replacing all heterozygous alleles with the corresponding reference alleles and maps 
the modified reads back to another personalized reference genome that contains only homozygous changes. The output of this step is a BAM 
file ready for any somatic mutation callers to use. We intend to offer long-term maintenance for PRESM and continue adding our new 
functions into it.
  
