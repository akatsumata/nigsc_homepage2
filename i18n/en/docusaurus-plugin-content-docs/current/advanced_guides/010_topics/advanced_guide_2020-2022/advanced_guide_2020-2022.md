---
id: advanced_guide_2020-2022
title: "Topics before 2022"
---


---

## NBDC-DDBJ Imputation Server (beta) 

18 Oct 2022.

The **Imputation Server** is a service to support imputation analysis of SNP array data. **[&#x1f517;Michigan Imputation Server](https://imputationserver.sph.umich.edu/)** and **[&#x1f517;TOPMed Project Imputation Server](https://imputation.biodatacatalyst.nhlbi.nih.gov/#!)** are public. These servers are located outside Japan and genomic data (SNP array data) had to be uploaded to the servers outside Japan for use.

Therefore, **[&#x1f517;the Department of NBDC Program of the Japan Science and Technology Agency](https://biosciencedbc.jp/en/)** has developed **the NBDC-DDBJ Imputation Server** system as a Japanese version of the imputation server that is easy for Japanese researchers to use. This system is currently available in **[the Personal Genome Analysis division](https://sc.ddbj.nig.ac.jp/en/personal_genome_division/pg_introduction)** of **[the NIG supercomputer system](https://sc.ddbj.nig.ac.jp/en/)**.

The imputation workflow used in this server was modified and implemented as a web service by the Department of NBDC Program with reference to the information (selection of imputation software and setting of parameters) provided by the National Center for Global Health and Medicine in the following AMED project The NBDC Business Promotion Department has modified and implemented it as a web service using this information as a reference. 

Project name: Platform Program for Promotion of Genome Medicine (Research and development research to resolve issues related to international data sharing) 

Subject name: "Investigation and practice of ethical and technical issues in genomic medical science research using cloud computing environment"

<table>
<tr>
<td width="400">


![](imputationserver.Fig1-work.png)

</td>
<td valign="top">

The NBDC-DDBJ Imputation Server (beta version) (hereafter referred to as 'this system') is available in the Personal Genome Analysis division of the NIG supercomputer. Researchers(users) can upload their own genome data to the server and execute the imputation analysis workflow via the web user interface.


- [NBDC-DDBJ Imputation Server](/advanced_guides/TogoImputation/imputation_server)
- [Install Manual](/advanced_guides/TogoImputation/imputation_server_install)
- [Tutorial](/advanced_guides/TogoImputation/imputation_server_tutorial)


</td>
</tr>
</table>





---
## PortablePipeline

10 May 2022.

For the NGS analysis pipeline, the tool called Portablepipeline has been developed by Professor Kazutoshi Yoshitake of the Laboratory of Aquatic Molecular Biology and Biotechnology, Aquatic Bioscience, Graduate school of Agricultural and Life Sciences, The Univresity of Tokyo.

For instructions on how to run the tool, refer &#x1f517;<a href="https://www.suikou.fs.a.u-tokyo.ac.jp/blog/2022/04/28/%e9%81%ba%e4%bc%9d%e7%a0%94%e3%81%ae%e3%82%b9%e3%83%91%e3%82%b3%e3%83%b3%e3%81%a7%e6%89%8b%e8%bb%bd%e3%81%abngs%e8%a7%a3%e6%9e%90%e3%82%92%e5%ae%9f%e8%a1%8c%e3%81%99%e3%82%8b%e6%89%8b%e9%a0%86/"> Laboratory of Aquatic Molecular Biology and Biotechnology page</a>.

<table>
<tr>
<td width="400">

![](portablepipeline.png)
</td>
<td valign="top">
"PortablePipeline is software that allows Windows and Mac users to perform NGS analysis in a GUI on a local or remote server or supercomputer. If python3 and docker or singularity are installed as an analysis server,  you run it instead of the supercomputer."（Referenced from the Laboratory of Aquatic Molecular Biology and Biotechnology）
</td>
</tr>
</table>


---

## DFAST

2 Oct 2022.

DFAST is an automated annotation tool for prokaryotic genome created by Assistant Professor, Yasuhiro Tanizawa of the Nakamura Group・Genome Informatics Laboratory at the National Institute of Genetics. This tool can also generate files for genome sequence registration to DDBJ. There is a web version available at https://dfast.ddbj.nig.ac.jp that can be used simply by uploading files, and a stand-alone version that can be run by command operation.

<table>
<tr>
<td width="400">

![](dfast.png)
</td>
<td valign="top">
To run the stand-alone version on the NIG supercomputer, there are two ways: get the source code from &#x1f517;<a href="https://github.com/nigyta/dfast_core/">https://github.com/nigyta/dfast_core/ </a> and install it (requires Python 3.6 or later and Biopython) or use the singularity container provided by the NIG supercomputer (ref: &#x1f517;<a href="https://qiita.com/nigyta/items/e1de21f6ece65d69ec1d">https://qiita.com/nigyta/items/e1de21f6ece65d69ec1d</a>).

</td>
</tr>
</table>

---

## Rhelixa RNAseq pipeline

08 Sep 2020.

The RNA-seq analysis pipeline has been provided by [&#x1f517;Rhelixa Corporation](https://www.rhelixa.com/) (CTO: Ryu Nakaki), which has a comprehensive collaboration agreement with the National Institute of Genetics, and implemented on the NIG supercomputer system.

This pipeline maps the Sequence Read Archive of a single sample obtained by the RNA-seq application to a reference genome, aggregates them by gene region and calculates the expression levels of all genes.

<table>
<tr>
<td width="400">

![](Rhelixa_RNAseq1_EN.png)

</td>
<td valign="top">

The RNAseq pipeline of Rhelixa is installed on the NIG supercomputer in the form of the Singularity container image. The Singularity container image cannot be used outside the NIG supercomputer. Check to the link below for instructions on how to use it.<br />
<br />

- [Rhelixa RNAseq > Introduction](/advanced_guides/Rhelixa_RNAseq/Rhelixa_RNAseq)
- [Rhelixa RNAseq > User manual](/advanced_guides/Rhelixa_RNAseq/Rhelixa_RNAseq_manual)

</td>
</tr>
</table>



