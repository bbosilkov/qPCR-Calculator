
# qPCR Fold Change Calculator

A step-by-step Jupyter notebook that turns raw RT-qPCR **Ct values** (mRNA) into **fold change** using the
Livak **2^-ΔΔCt** method, then plots the result.

Example: IL6 expression in **Tumour vs Control** tissue, normalised to GAPDH + ACTB.

## Steps in the notebook
1. Raw Ct values (one row per well: `sample, group, gene, ct`)
2. Quality check of technical replicates (SD > 0.3, Ct > 35)
3. Average technical replicates
4. Reference Ct (mean of reference genes)
5. ΔCt = Ct(gene of interest) − Ct(reference)
6. ΔΔCt = ΔCt − mean ΔCt(control)
7. Fold change = 2^-ΔΔCt
8. Group summary + t-test on ΔCt
9. Bar chart with individual replicates
10. Whole calculator as one function + self-check

## Run it
```bash
pip install -r requirements.txt
jupyter lab qPCR_fold_change_calculator.ipynb
```

To use your own data, replace the example table in Step 1 with `pd.read_csv("your_file.csv")`
(columns: `sample, group, gene, ct`).

## Notes
- Assumes ~100% amplification efficiency for all genes (use the Pfaffl method if not).
- The example Ct values are made up for demonstration.

## References
- Livak & Schmittgen, *Methods* 2001;25:402–408
- Schmittgen & Livak, *Nature Protocols* 2008;3:1101–1108
- Vandesompele et al., *Genome Biology* 2002;3:research0034
- Bustin et al. (MIQE), *Clin Chem* 2009;55:611–622

## License
MIT — see [LICENSE](LICENSE).
