## About this browser

Single-cell proteomics (SCP-MS) of mouse distal convoluted tubule (DCT) cells on a control diet and on a zero-potassium (zero-K) diet, as reported in the accompanying manuscript (title and DOI to be added on publication).

- Raw data: ProteomeXchange / PRIDE **PXD087695**.
- Processed objects: Zenodo, [doi.org/10.5281/zenodo.24365599](https://doi.org/10.5281/zenodo.24365599).
- Code: [github.com/qiwu-au/scp_mouse_kidney_dct](https://github.com/qiwu-au/scp_mouse_kidney_dct).

### Experiment

- **Diets:** control diet or zero-K diet for 4 days.
- **Mice:** one pool of three parvalbumin-eGFP mice per condition. Condition and pool cannot be separated, and cells are not animal-level replicates.
- **Sort plates:** the cells of each pool were sorted onto two plates (P1, P2). Plates are technical, not biological, replicates.
- **Search:** the runs of both conditions were searched together in one Spectronaut search (library-free; 1% precursor and protein FDR; cross-run normalization over all runs; no imputation). A protein group is therefore the same in both conditions.

### Data

| | Control | Zero-K |
| --- | --- | --- |
| Cells acquired | 768 | 767 |
| Cells retained (at least 100 detected proteins) | 729 | 702 |
| Protein groups kept (detected in at least 2 retained cells of the condition) | 6,078 | 5,953 |

- The export holds 6,208 protein groups; 5,897 are kept in both conditions.
- **Intensities:** Spectronaut PG.Quantity per cell. "Detected" means intensity > 0.
- **UMAP:** one per condition.
  - Analysis matrix: ln(1 + intensity), z-scored per protein over the cells of the condition and clipped at ±10.
  - Neighbour graph: k = 10 on 20 principal components.
  - The UMAP is the embedding of that graph. It was computed without the cell labels.

### Cell types (cluster annotation)

- **Clustering:** Leiden 1.0 clusters on the neighbour graph of each condition (seed 42; minimum 5 cells).
- **Naming:** each cluster is named from its differential proteins (that cluster vs all other cells of the condition) and the DCT marker list (Supplementary Table S2). Slc12a3 and Umod count as shared markers.
- **Counts:**
  - Control: DCT1 382, DCT2 85, DCT, subtype not resolved 262.
  - Zero-K: DCT1 449, DCT, subtype not resolved 253.
- **DCT, subtype not resolved:** cells of clusters without a DCT1 or DCT2 marker among their differential proteins.
- **Not found at cluster level:** no cluster was annotated as ProLIF in either condition, and no zero-K cluster as DCT2.
- **Markers not quantified:** Col5a2 and Cenpf.
- **Protein depth:** the clusters differ in the number of proteins per cell (the *Clusters and their marker evidence* table on the Overview page gives the median per cluster).
- **Label seeds:** 569 of 729 control cells and 479 of 702 zero-K cells keep their label in ten further Leiden seeds.

### ProLIF cells (per-cell proliferation test)

- ProLIF cells are called per cell, separately from the cluster annotation.
- A cell is called cycling when more of 36 S- and G2/M-phase proteins are detected in it than in cells of similar depth, judged against 1,000 random protein sets of matched detection rate (Benjamini–Hochberg q < 0.05). It is ProLIF when Slc12a3 is also detected. Mki67 and Top2a are not used.
- **Counts:** control 37 of 729 cells; zero-K 63 of 702 cells.
- The label set *Cell types with ProLIF cells* shows these cells as their own group; the other cells keep their cluster annotation.

### Label transferred from control cells (zero-K only)

- Each zero-K cell takes the most frequent cluster annotation of its ten nearest control cells in a joint 20-component embedding of both conditions.
- **Counts:** DCT1 398, DCT2 68, DCT, subtype not resolved 236.
- It cannot carry ProLIF, because no control cluster is annotated as ProLIF.

### Control vs zero-K

- The page compares the 5,897 protein groups kept in both conditions.
- The counts and summaries per condition are computed by the browser and involve no test.
- The reported results (two-part test of detection and intensity, each adjusted for the number of proteins per cell; pre-specified panel) are the stored values of Supplementary Table S18 of the manuscript, for the cells annotated DCT1 or DCT2 (467 control, 449 zero-K).
- With one pool of three mice per condition, condition and pool cannot be separated, and every p and q value is descriptive.

### How values are computed

- **Detection rate:** the fraction of a cell type's cells with intensity > 0.
- **Median intensity:** computed over the detected cells only.
- **Mean ln(1 + intensity):** computed over all cells of the cell type, with not-detected cells counted as 0.
- **Dotplots:**
  - Size is the detection rate.
  - Colour is the cell-type mean of the per-protein z-scored ln(1 + intensity), rescaled 0–1 per protein across the plotted rows.
  - On the single-condition pages the z-score is over the cells of that condition; on the comparison page it is over the cells of both conditions.
  - For the control cells, the first marker preset under *Cell types with ProLIF cells* reproduces the protein values of the manuscript's DCT marker dotplot (differences below 10⁻⁶).
- **Core & Unique:**
  - Core = detected in at least Y% of a cell type's cells.
  - Unique = Core in at most X% of the other selected cell types.

### Version

The data files were built from the analysis objects by the browser's data build scripts. The build dates and the checksum of every data source are in the build information files (Downloads page; *Control vs zero-K* page, Downloads tab).
