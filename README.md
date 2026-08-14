# inflammation-enrichment

A set of inflammatory genes processed via [KEGG mapping](https://www.genome.jp/kegg/kegg1b.html).

## Overview

The pipeline performs the following analyses:

* Converts HGNC gene symbols into UniProt and GeneCards identifiers using R ```biomaRt```.
* Identifies missing or ambiguous annotations for manual curation.
* Performs KEGG over-representation analysis (ORA) using ```clusterProfiler```.
* Maps genes to KEGG IDs, KEGG Orthologs (KOs), and KEGG pathways through the KEGG REST API (R ```KEGGREST```).
* Calculates a local pathway enrichment based on gene-pathway associations and evaluates significance using the hypergeometric test with Benjamini–Hochberg correction (p-value adjusted).
* Generates preliminary visualizations of pathway distributions, enrichment results, and highly connected inflammatory genes.
* Explores KEGG pathway topology using ```KEGGgraph``` and ```Rgraphviz``` to identify central genes within pathway networks.

## Input Data


```inflammation_genes.tsv``` — Initial list of inflammatory genes (HGNC symbols).

```curated_genes.tsv``` — Curated gene catalog containing UniProt and GeneCards identifiers.

## Output

The analysis produces:

* Curated gene annotation tables.
* KEGG pathway mappings.
* Enrichment statistics and p-values.
* Summary plots of pathway distributions and enrichment.
* Network visualizations of selected KEGG pathways.

## Notes

The workflow uses the current KEGG REST API for pathway annotations. Because the KEGG database is updated regularly, pathway names and annotations may change over time. Some newly introduced pathways are manually curated to ensure compatibility with the analysis.
