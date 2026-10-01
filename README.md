# What makes a molecule smell? Structure–odor cliffs in odorant molecules

Cheminformatics analysis of how small changes in molecular structure relate to large changes in odor perception.

**Research question:** What molecular changes drive discontinuities ("cliffs") between chemical structure and odor perception?

**Author:** Stella Tsiourva
**Project:** 3-month internship at CGLab, July–September 2026

## Resources

| Resource | Description | Link |
|---|---|---|
| 📊 Data | 754 odorant molecules: `InChIKey`, `SMILES`, `Odors` (comma-separated odor descriptors; some molecules have none) | [inchi_smiles_odors.csv](inchi_smiles_odors.csv) |
| 💻 Code | Full analysis notebook (Python, RDKit; outputs included) | [m2or_odorants_analysis.ipynb](m2or_odorants_analysis.ipynb) |
| 🎤 Presentation | Project slides (PDF) | [What_makes_a_molecule_smell.pdf](What_makes_a_molecule_smell.pdf) |

## What the notebook does

1. Computes physicochemical properties (MW, cLogP, TPSA, HBD/HBA, ...) and functional groups with RDKit.
2. Builds a molecule × odor-word table and relates it to properties and functional groups.
3. Computes Morgan fingerprints (radius 2, 2048 bits), Tanimoto similarity and Butina clustering (threshold 0.6).
4. Scores odor agreement within clusters (Jaccard) to find structure–odor discontinuities.
5. Scans all molecule pairs for cliffs (structural similarity ≥ 0.5, odor similarity ≤ 0.1) and tallies which structural changes cause them (chain length, ester/ether, carboxyl, ketone, sulfur, stereochemistry, ...).

## Usage

```bash
git clone https://github.com/cgenomicslab/odorant-cliffs.git
cd odorant-cliffs

conda create -n odor-rdkit -c conda-forge python rdkit pandas numpy matplotlib jupyter
conda activate odor-rdkit
jupyter notebook m2or_odorants_analysis.ipynb
```

Run the notebook from the repository root so it finds the CSV.

## Data source

M2OR DB
