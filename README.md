# ccle_extractor
Extracting gene expression/metabolomics datasets from [CCLE](https://portals.broadinstitute.org/ccle) database

## Requirements
> - [pandas](https://pandas.pydata.org)
> - [matplotlib](https://matplotlib.org)
> - [seaborn](https://seaborn.pydata.org)

## CCLE Data
- CCLE_RNAseq_rsem_genes_tpm_20180929.txt.gz
- Cell_lines_annotations_20181226.txt
- CCLE_RNAseq_genes_counts_20180929.gct.gz
- CCLE_metabolomics_20190502.csv

## Usage
1. Gene expression data
    ```python
    from ccle_processing import CancerCellLineEncyclopedia as CCLE

    # Set gene_nemes
    # Set ccle_names or cell_lines

    selected_CCLE_subset = CCLE(
        gene_names = ['EGFR', 'ERBB2', 'ERBB3', 'ERBB4'],
        ccle_names = ['MCF7_BREAST', 'MDAMB231_BREAST']
    )

    ''' or
    selected_CCLE_subset = CCLE(
        gene_names = ['EGFR', 'ERBB2', 'ERBB3', 'ERBB4'],
        cell_lines = ['MCF7', 'MDA-MB-231']
    )
    '''

    # GeneCards link (https://www.genecards.org)
    selected_CCLE_subset.to_gene_summary()
    # TPM value
    selected_CCLE_subset.to_gene_expression()
    ```
1. Metabolomics dataset
    ```python
    from ccle_processing import CancerCellLineEncyclopedia as CCLE

    # Set metabolite_nemes
    # Set ccle_names or cell_lines

    selected_CCLE_subset = CCLE(
        metabolite_names = ['lactate', 'glutamine', 'glutamate', 'serine', 'alanine'],
        ccle_names = ['MCF7_BREAST', 'MDAMB231_BREAST']
    )

    # Metabolite levels
    selected_CCLE_subset.to_metabolomics()
    ```

## Output
- gene_summary.md
- tpm_values.csv
- gene_expression/
- metabolite_levels.csv
- metabolomics/

## Installation
    $ git clone https://github.com/okadalabipr/CCLEctor.git

## License
[MIT](LICENSE)