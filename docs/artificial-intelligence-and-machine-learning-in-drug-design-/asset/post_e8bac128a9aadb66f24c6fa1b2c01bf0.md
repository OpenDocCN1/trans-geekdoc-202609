
understanding biological data, computational methods are utilized. In bioinformatics, genomic, proteomic, and metabolomics data are handled, all of which are topics covered in this chapter.

This chapter discusses some of the most significant uses of bioinformatics. In it, topics such as genomic sequencing, predicting the functions of genes and proteins, analyzing biological networks and pathways, drug discovery and design, predicting diseases, and personalized medicine are covered. The fundamental approaches and techniques used in bioinformatics are also discussed. Among these are machine learning, sequence alignment search, phylogenetic analysis, molecular modeling and simulation, and phylogenetic tree reconstruction.

In addition to this, the chapter discusses the necessity for powerful computational resources in the field of bioinformatics as well as data privacy and heterogeneity. It provides a glimpse of the field's potential. In the final part of the chapter, the primary software, databases, and tools of bioinformatics are discussed, demonstrating how theory is used in practice. This chapter provides an overview of bioinformatics, including its significance, uses, and challenges. It lays the groundwork for a more in-depth investigation of this topic in subsequent chapters.

## 3.1.1 Medical Data

Bioinformatics organizes and retrieves biological databases. These databases contain DNA, protein, gene annotations, protein structures, pathways, and more.

GenBank has DNA sequences from numerous animals. Genomics involves gene, genome, and EST annotations. GenBank stores all published nucleotide sequences and protein translations. NCBI and the International Nucleotide Sequence Database Collaboration (INSDC) maintain this database. GenBank and its colleagues receive sequences from over 100,000 organisms from labs worldwide. Scientists can explore the database for genomic sequences of thousands of animals and species for their research.

### GenBank

It contains genetic sequencing, EST, STS, and other data. Researchers in academia and industry utilize GenBank for phylogenetics, protein sequence/function prediction after gene expression, and protein structure modeling. In conjunction with ENA and DDBJ, GenBank provides sequence data. To create a global database, the three groups collect a percentage of the sequence data published worldwide and share it. Automated annotation systems, sequence submitters, and database curators collaborate to annotate sequences and maintain database quality. GenBank strives to assure data accuracy; however, it does not verify annotations.

### UniProt (protein sequences)

Several sources list protein names, functions, domains, and post-translational modifications. Data about protein sequences and annotations can be found in the Universal Protein Resource, also known as UniProt. It is a project that is worked on jointly by the EBI, SIB, and PIR. The UniProt database is a resource for scientists that is free, comprehensive, and of a high quality. It focuses on the sequence and function of proteins. The database contains proteins that have been described as well as those that are anticipated. The information that can be found on this central hub for protein function is precise, consistent, and extensive. It is divided into two sections: one that has been manually reviewed and is called UniProtKB/Swiss-Prot and the other is called TrEMBL. Sequences from UniProtKB and UniParc are grouped together in this database, which allows for coverage of the sequence space at many resolutions while hiding repetitive sequences. The protein sequences obtained from a variety of sources, including those stored in other databases, are reliable and comprehensive. Updated databases are made available by the UniProt project every 4 weeks in order to refine and enrich the data. Researchers studying a single protein as well as those studying complex biological systems make use of UniProt.

### PDB

It stores experimental protein, nucleic acid, and complex-assembly three-dimensional structures. Structural biology examines protein structures, interactions, and drug design. Proteins and nucleic acids (DNA and RNA) have three-dimensional structural data in the Protein Data Bank (PDB). Experimental methods like X-ray crystallography, NMR spectroscopy, and cryo-electron microscopy reveal these molecules’ shape and organization, revealing their cell functions and interactions. The Worldwide Protein Data Bank (wwPDB) manages the PDB, which was founded in 1971 by the Research Collaboratory for Structural Bioinformatics (RCSB) in the US, the Protein Data Bank Europe (PDBe), the Protein Data Bank Japan (PDBj), and BioMagResBank (BMRB).

The PDB helps bioinformaticians, structural biologists, computational chemists, and other scientists develop new drugs and therapies, design novel proteins with tailored functions, and teach structural biology. Academics and students can freely obtain structural data from the PDB database. Users can study the three-dimensional structure of molecules using molecular graphics software.

### Ensembl

This genome browser and annotation database annotates multiple genomes. It shows genes, regulatory elements, genetic variants, and comparative genomics. Ensembl is a big, high-quality genetic database. EBI and Wellcome Trust Sanger Institute maintain it. Ensembl intends to centralize genome-wide data from vertebrates and model animals for researchers. It aids researchers in gene function analysis. Ensembl includes genome structure, gene variants (such as SNPs), gene expression, comparative genomics, and more. It funds research on disease, pharmaceuticals, evolution, and biodiversity.

The Ensembl browser lets people visualize data in the genome and view a genomic area, gene structures, variations, and species genomes. Ensembl also offers sequence alignment and variation effect prediction bioinformatics tools and APIs. As of September 2021, Ensembl supports data from over 100 species, including humans, mice, zebrafish, and others, and its resources are free and updated monthly.

### KEGG

It contains genetic, chemical, and systemic functioning data. Pathways, illnesses, therapeutics, and molecular interactions are studied. Kyoto Encyclopedia of Genes and Genomes (KEGG) incorporates genomic, chemical, and systemic functional data. It is maintained by Japan's Kyoto University Bioinformatics Centre. KEGG's databases and tools let researchers understand the cell, organism, and ecosystem's high-level functions and utility from molecular data. Pathways, genetic information, and higher-level systemic processes can be examined in these biological systems.

The KEGG PATHWAY database depicts biological processes like metabolism, genetic information processing, environmental information processing, organismal systems, and human diseases. These pathways encapsulate current molecular interaction knowledge and can be utilized for data visualization, high-throughput data interpretation, and teaching. As of September 2021, researchers worldwide use KEGG for genomes, transcriptomic, proteomics, and metabolomics.

### Reactome (selected biological pathways)

It covers metabolism, signaling, and gene regulation. Reactome is a free, open-source, curated, and peer-reviewed biological pathway database. It provides intuitive pathway visualization, interpretation, and analysis bioinformatics tools. Reactome is an organized network of chemical changes that describes signal transmission, transport, DNA replication, metabolism, and other biological functions. Reactome emphasizes human biology and model organisms. The database lets researchers compare the high-level operations of the human biological system to other species. The Ontario Institute for Cancer Research in Canada, the European Bioinformatics Institute in the UK, and New York University Langone Medical Centre in US collaborated on Reactome project.

Reactome, like other pathway databases, lets academics analyze their data inside recognized pathways. This can reveal a dataset's biological functionalities. Reactome data, including scientific literature, are manually selected for accuracy and relevance. The database is updated with biological research findings. Reactome, used in genomics, proteomics, and systems biology, contains information on thousands of events involving tens of thousands of proteins and tiny chemicals as of September 2021.

### EMBL databases

EMBL-Bank has nucleotide sequences, while EMBL-EBI contains protein sequences, gene expression data, and functional genomics data.

Bioinformatics provides computational methods for biological data analysis. These methods include data storage, retrieval, analysis, modeling and simulation, and visualization. Bioinformatics' first problem is managing massive biological data from genome sequencing, proteomic analysis, and other high-throughput methods. Bioinformaticians create GenBank for DNA sequences and Protein Data Bank for protein structures to manage this data. These databases store, retrieve, and share biological data efficiently as well as analyze data after storing it. This may entail matching novel sequences with existing ones to detect similarities and differences.

Bioinformatics simulates biological systems, from modeling the ecology to modeling a protein's 3D structure. Molecular dynamics simulations can predict atom movement and interaction. Bioinformatics requires visualization. It helps interpret complex biological data and can uncover patterns and insights not immediately obvious from raw data. PyMOL is used for molecular structures and Cytoscape for biological networks. Bioinformatics turns biological data into useful information. It turns huge, complex, and seemingly incoherent data into useful insights for biological and medical research using computer methods.

## 3.1.2 Sequence Alignment and Searching

Bioinformatics aligns DNA, RNA, and protein sequences to find commonalities, trends, and functions. These processes are needed for sequence conservation, evolutionary links, protein structure prediction, and gene or protein recognition. These algorithms align using match scores, mismatch penalties, and gap penalties. Sequences are aligned pairwise. MSA residue conservation aligns three or more sequences. MSA algorithms include ClustalW, MUSCLE, and T-Coffee. MSA determines evolutionary links, conserved areas, and protein structures. BLAST compares query sequences to sequence databases, quickly finds local sequence similarities, and delivers matched significance E-values [1].
