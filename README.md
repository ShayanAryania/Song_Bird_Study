The Song Bird Study

### Introduction

#### Investigating the Influence of Social Environment on Neural Responses to Sickness in Zebra Finches: A Bioinformatics Approach

The Zebra Finch, _Taeniopygia guttata_, a widely used model organism in behavioral and neurobiological research, provides an excellent platform to study the interplay between social environment, neural function, and immune response. In this project, we delve into an intriguing scientific question: How does the social environment of these birds modulate their neural response to immune challenges?

This question was explored in a study by Lopes PC, Faber-Hammond JJ, Siemonsma C, Patel S, and Renn SCP, titled _"The social environment alters neural responses to a lipopolysaccharide challenge"_ (Brain Behav Immun 2023). Their research demonstrated that the social environment, particularly the presence of conspecifics, could significantly modulate the neural responses of Zebra Finches to immune challenges such as lipopolysaccharide (LPS), a molecule known to induce immune responses. Link to Paper

Our goal in this notebook is to revisit and build upon the findings of this study. Using RNA sequencing data from their research, we aim to conduct a comprehensive analysis of changes in gene expression across different brain regions of Zebra Finches under different social conditions. We will specifically focus on the hypothalamus, the bed nucleus of the stria terminalis, and the nucleus taeniae, all of which are key regions for understanding behavior and immune response.

The essence of this project is to draw meaningful insights from high-dimensional data. We encourage you to start with basic approaches and gradually build complexity. Remember, every effort to extract information and gain insights from the data is valuable and will be recognized. Approach the tasks with curiosity and an open mind, and let your analytical journey be both informative and enjoyable.

---
### Experiment Design

The primary aim of this high-throughput sequencing study was to discern how different social environments could modulate the neural response to sickness induced by lipopolysaccharide (LPS).

**Lipopolysaccharide (LPS)** is a large molecule consisting of a lipid and a polysaccharide, found in the outer membrane of Gram-negative bacteria. It is often referred to as an endotoxin due to its ability to trigger strong immune responses. When a Gram-negative bacterium dies, it releases its LPS, which can then find its way into the bloodstream. In the context of this study, LPS was used to simulate an immune challenge or sickness in the Zebra Finches.

**The Experimental Setup:**

The experiment involved male Zebra Finches, which were administered either an LPS injection to simulate sickness or a control solution. Following the injection, the birds were placed in one of four distinct social contexts:

- **Isolated (ISO)**: In this setting, the birds were kept alone without a female. This condition was designed to examine the neural and immune responses of the birds in the absence of any social interactions. This group helps to understand the baseline responses to the LPS challenge when there are no social factors at play.
- **Known Female Continuous (KFC)**: Here, the birds were continuously housed with a known female. This condition allowed the researchers to investigate the effects of a stable social environment on the birds' responses to the LPS challenge. This group can provide insights into how ongoing social interactions might influence the response to sickness.
- **Known Female Reunited (KF)**: In this scenario, the birds were reunited with a known female after a period of separation. This condition was intended to mimic the effects of a disrupted social environment followed by a reunion. This group can shed light on how changes in social relationships might affect the neural and immune responses to sickness.
- **Novel Female (NF)**: In this context, the birds were paired with a previously unknown female. This condition was designed to explore the effects of introducing a new social partner on the birds' responses to the LPS challenge. This group can reveal how novel social encounters might modulate the response to sickness.

These social settings were carefully chosen to represent a range of social interactions that the birds might encounter in their natural habitats. The experimental design allows for a comprehensive investigation of how social environment influences the neural responses to sickness, thereby improving our understanding of how the social environment can affect health.

---
### Understanding RNA-Seq

RNA-Seq (RNA sequencing) is a powerful technique that uses next-generation sequencing (NGS) to reveal the presence and quantity of RNA molecules in a biological sample. It provides a snapshot of gene expression, also known as the transcriptome.

**What is RNA-Seq?**

RNA-Seq allows us to investigate and discover the transcriptome, which is the total cellular content of RNAs including mRNA, rRNA, and tRNA. Understanding the transcriptome is key if we are to connect the information in our genome with its functional protein expression. RNA-Seq can tell us which genes are turned on in a cell, what their level of transcription is, and at what times they are activated or shut off. This allows scientists to understand the biology of a cell more deeply and assess changes that may indicate disease.

**How does RNA-Seq work?**

The RNA-Seq workflow has several steps:

1. **RNA extraction**: The first step involves extracting the total RNA from the sample.
2. **Reverse transcription into cDNA**: The extracted RNA is then converted into complementary DNA (cDNA) through a process called reverse transcription.
3. **Library preparation**: The cDNA is then used to prepare a sequencing library. This involves fragmenting the cDNA, adding sequencing adapters, and amplifying the library.
4. **Sequencing**: The prepared library is then sequenced using high-throughput sequencing technology.

**RNA-Seq Data**

The output of an RNA-Seq experiment is a large set of short DNA sequences, or reads. These reads can be aligned to a reference genome to determine which genes were being transcribed at the time the sample was collected. The number of reads aligning to a particular gene provides a measure of that gene's expression level.

**RNA-Seq vs Microarrays**

RNA-Seq has several advantages over microarray technology, a legacy technology often used in gene expression studies. Unlike microarrays, which require species- or transcript-specific probes, RNA-Seq does not require any prior knowledge about the sequences of the transcripts. This allows RNA-Seq to detect novel transcripts, gene fusions, single nucleotide variants, indels (small insertions and deletions), and other previously unknown changes. RNA-Seq also has a wider dynamic range and higher sensitivity compared to microarrays, making it better at detecting transcripts and specifically isoforms.

<blockquote style="font-family:Arial; color:red; font-size:16px; border-left:0px solid red; padding: 10px;">
    <strong>Don't forget to answer these questions!</strong>
</blockquote>

**Questions**

1. Why is it important to convert RNA into cDNA for RNA-Seq? What would happen if we tried to sequence RNA directly?
2. How does the process of preparing a sequencing library contribute to the accuracy of RNA-Seq results? What are some potential sources of error in this step?
3. How does the ability of RNA-Seq to detect novel transcripts contribute to our understanding of gene function? Can you think of a scenario where this capability would be particularly useful?
4. Why might a researcher choose to use RNA-Seq instead of microarrays for a gene expression study? What are some potential advantages and disadvantages of each method?


**_Your Answer:_**:

**Question 1:**  
Transforming RNA into cDNA is often a critical step in RNA-Seq due to several factors:

- RNA's single-stranded structure makes it more susceptible to degradation by RNAse enzymes, unlike cDNA's double-stranded form, which is notably more stable and amenable to PCR amplification. This process enables the identification and quantification of transcripts that are present in low amounts.
- The majority of high-throughput sequencing technologies are optimized for DNA, not RNA. By converting RNA into cDNA, researchers can apply these powerful DNA-sequencing tools to analyze the transcriptome.
- Sequencing RNA directly necessitates the use of specific protocols and enzymes tailored for single-stranded RNA molecules, adding complexity and potential technical hurdles to the process.


**Question 2:**  
### Steps in preparing a library:

- Extracting and purifying RNA: It's crucial to obtain pure, intact RNA from samples to avoid biases in transcript representation caused by contaminants or degradation.

- Fragmenting RNA: Cutting RNA into smaller pieces aids in library preparation and sequencing, but non-uniform fragmentation may bias the library towards certain transcript lengths.

- Synthesizing cDNA: RNA fragments are first reverse transcribed into single-stranded cDNA, which is subsequently converted to double-stranded cDNA. Mistakes in this phase, such as primer bias or incomplete synthesis, can affect gene expression analysis.

- Attaching adapters: Both ends of the cDNA are tagged with short adapter sequences, essential for further amplification and sequencing. Incorrect ligation can produce chimeric sequences or incomplete libraries.

- Amplifying PCR: This step increases the quantity of the cDNA library for sequencing. Excessive amplification can introduce errors in the sequence and distort expression profiles.

### Sources of error:

- Biased RNA extraction: Varying cell types in a sample or flawed extraction methods can unfairly represent certain transcripts.
- Bias in fragmentation: A preference for breaking up certain RNA lengths can influence expression measurements towards those transcripts.
- Primer bias: Primers in reverse transcription may selectively bind to specific sequences, inaccurately reflecting gene presence.
- Inadequate cDNA synthesis: Partial cDNA creation can result in absent or incomplete transcripts in the library.
- Formation of chimeric sequences: Incorrect adapter attachment can link fragments from unrelated genes, creating misleading sequences.
- Bias in PCR amplification: Disproportionate amplification of cDNA fragments can misrepresent expression levels.


**Question 3:**  
The detection of unknown transcripts enables researchers to:

- Bridge knowledge gaps in gene functions by identifying new elements involved in cellular activities.
- Deepen understanding of gene regulation through exploring the intricate mechanisms that control gene activity.
- Link genes with diseases by pinpointing new diagnostic and therapeutic targets.
- Explore the evolutionary development of genes to understand how organisms adapt and evolve.

### Exploring human disease:

- Investigating a rare genetic disorder known to be caused by a specific gene might not fully explain all symptoms through standard analysis. Utilizing RNA-Seq to examine patient samples could uncover new transcripts from the affected gene, potentially revealing proteins or regulatory disruptions not previously known. These findings might complete the understanding of the disease and highlight novel treatment avenues.


**Question 4:**  
Choosing between RNA-Seq and microarrays depends on the research objectives and financial considerations. Key aspects to consider include:

- Purpose of the study: For research focusing on discovering new transcripts or analyzing genes of low abundance, RNA-Seq is typically more suitable.
- Budget constraints: Microarrays offer a less costly alternative for those with limited funding.
- Expertise requirements: Those with minimal bioinformatics skills may find microarray analysis to be more straightforward.
- Size of the study: For smaller-scale studies, microarrays could be more appropriate, whereas RNA-Seq may be preferred for larger datasets.

### RNA-Seq:

**Pros:**

  - Unbiased detection capabilities allow for the identification of all RNA species in a sample, including novel transcripts, alternative splicing variants, and non-coding RNAs, which might be overlooked by microarrays.
  - Superior sensitivity enables the detection of transcripts present in small quantities, offering a fuller overview of the transcriptome.
  - A broader dynamic range permits accurate gene expression measurement across a vast spectrum of expression levels.
  - Versatility due to the lack of reliance on pre-designed probes, making it adaptable to any species or research question.

**Cons:**

  - Generally, RNA-Seq is more costly than microarrays, encompassing both operational and analysis expenses.
  - Analyzing RNA-Seq data demands more sophisticated bioinformatics knowledge.
  - RNA-Seq produces a significantly larger volume of data, requiring extensive storage and processing capabilities.

### Microarrays:

**Pros:**

  - Microarrays are less expensive compared to RNA-Seq, in terms of both setup and analysis.
  - Analysis of microarray data is generally simpler and less time-consuming.
  - Experiments using microarrays can be conducted and analyzed more swiftly than those involving RNA-Seq.
