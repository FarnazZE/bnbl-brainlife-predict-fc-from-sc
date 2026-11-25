<h1 align="center">Predict functional connectivity from structural connectivity</h1>

<p align="center">
  Computes binary and weighted structural-connectivity predictors (path length, communicability, cosine distance, mean first passage time, matching index, search information, path transitivity) and how well each predicts functional connectivity per brain region.
</p>

<p align="center">
  <a href="https://github.com/brainlife/abcd-spec"><img src="https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg" alt="ABCD Spec v1.1"></a>
  <a href="https://doi.org/10.25663/brainlife.app.646"><img src="https://img.shields.io/badge/Brainlife-brainlife.app.646-blue.svg" alt="Run on brainlife.io"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-see_LICENSE-lightgrey.svg" alt="License"></a>
</p>

## At a glance

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Computes binary and weighted structural-connectivity predictors (path length, communicability, cosine distance, mean first passage time, matching index, search information, path transitivity) and how well each predicts functional connectivity per brain region.**

Derives 14 network predictors from a structural connectivity matrix and, for every region, correlates each predictor with that region's functional connectivity profile, saving the squared correlations (r^2) per region and predictor. Use it to study local structure-function coupling. The code reads two connectivity matrices (structural first, functional second) from the conmat input although the input is registered as a single matrix, and it writes a CSV (output/csv/rsq.csv) although the output is registered as a PDF report.

| | |
|---|---|
| **Inputs** | `neuro/conmat` |
| **Outputs** | `report/pdf` |
| **Container** | `filsilva/cxnetwork:0.2.0` |
| **Resources** | 1 CPUs · 6 GB memory · 1 h walltime |
| **Run it** | [doi.org/10.25663/brainlife.app.646](https://doi.org/10.25663/brainlife.app.646) |

#### Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `conmat` | `neuro/conmat` | yes |  |

#### Outputs

| Output | Datatype | Description |
|---|---|---|
| `output` | `report/pdf` |  |

<details>
<summary><b>Parameters</b> (3)</summary>

| Parameter | Type | Default | Description |
|---|---|---|---|
| `gammavals` | number | `0.5` | convert edge weight to cost |
| `predictors` | enum | `all` | Which predictor to evaluate; 'all' evaluates all 14 binary and weighted predictors. Options: `all`, `PLbin`, `Gbin`, `Cosbin`, `mfptbin`, `MIbin`, `SIbin`, `PTbin`, `Gwei`, `Coswei`, `mfptwei`, `MIwei`, `SIwei`, `PTwei`, `PLwei`. |
| `remove nodes` | enum | `false` | remove isolated nodes (row/columns with all zero values) Options: `true`, `false`. |

</details>

<!-- brainlife-app:end -->

## Running the App

### On brainlife.io

Open the App at [doi.org/10.25663/brainlife.app.646](https://doi.org/10.25663/brainlife.app.646), choose `neuro/conmat` from your project, set the parameters and press **Execute**. The results are saved to your project as `report/pdf`.

### Locally

You need [Singularity/Apptainer](https://apptainer.org/) (the App runs in `filsilva/cxnetwork:0.2.0`), [`jq`](https://jqlang.github.io/jq/).

1. Clone this repository.
2. Create `config.json` with the paths to your inputs and the parameters:

   ```json
   {
       "index": "/path/to/conmat/index",
       "label": "/path/to/conmat/label",
       "csv": "/path/to/conmat/csv",
       "gammavals": 0.5,
       "predictors": "all",
       "remove nodes": "false"
   }
   ```

3. Run `./main`.

## Troubleshooting

- **connectivity matrix (network) should be fully connected**: Set 'remove nodes' to true to drop isolated nodes.

## Citing

If you use this App, please cite it, the software it builds on and brainlife.io:

- Predict functional connectivity from structural connectivity. brainlife.io App. [doi:10.25663/brainlife.app.646](https://doi.org/10.25663/brainlife.app.646)
- Esfahlani FZ, Faskowitz J, Slack J, Misic B, Betzel R. Local structure-function relationships in human brain networks across the human lifespan. bioRxiv (2021).
- Esfahlani, F. Z., Faskowitz, J., Slack, J., Misic, B., & Betzel, R. (2021). Local structure-function relationships in human brain networks across the human lifespan. bioRxiv.
- Hayashi S, Caron BA, Heinsfeld AS, et al. brainlife.io: a decentralized and open-source cloud platform to support neuroscience research. *Nature Methods* 21:809–813 (2024). [doi:10.1038/s41592-024-02237-2](https://doi.org/10.1038/s41592-024-02237-2)
- Avesani P, McPherson B, Hayashi S, et al. The open diffusion data derivatives, brain data upcycling via integrated publishing of derivatives and reproducible open cloud services. *Scientific Data* 6:69 (2019). [doi:10.1038/s41597-019-0073-y](https://doi.org/10.1038/s41597-019-0073-y)

## Authors

- [Farnaz Zamani Esfahlani]

<!-- ### Contributors
- [Richard F. Betzel]
- [Franco Pestilli]
- [Filipi Nascimento Silva]

## Funding

[![Wellcome-226486/Z/22/Z](https://img.shields.io/badge/Wellcome-226486%2FZ%2F22%2FZ-purple.svg)](https://wellcome.org/)
[![NIH-NINDS-U24NS140384](https://img.shields.io/badge/NIH_NINDS-U24NS140384-green.svg)](https://reporter.nih.gov/project-details/11261037)
[![NIH-NINDS-UM1NS132207](https://img.shields.io/badge/NIH_NINDS-UM1NS132207-green.svg)](https://reporter.nih.gov/project-details/11411328)
[![NIH-NIBIB-R01EB029272](https://img.shields.io/badge/NIH_NIBIB-R01EB029272-green.svg)](https://reporter.nih.gov/project-details/10262925)
[![NIH-NIBIB-R01EB030896](https://img.shields.io/badge/NIH_NIBIB-R01EB030896-green.svg)](https://reporter.nih.gov/project-details/10428625)
[![NIH-NIMH-R01MH126699](https://img.shields.io/badge/NIH_NIMH-R01MH126699-green.svg)](https://reporter.nih.gov/project-details/10460628)
[![NIH-NIDCD-R01DC020088](https://img.shields.io/badge/NIH_NIDCD-R01DC020088-green.svg)](https://reporter.nih.gov/project-details/11140284)
[![NSF-BCS-1734853](https://img.shields.io/badge/NSF_BCS-1734853-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1734853)
[![NSF-BCS-2203524](https://img.shields.io/badge/NSF_BCS-2203524-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2203524)
[![NSF-IIS-1636893](https://img.shields.io/badge/NSF_IIS-1636893-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1636893)
[![NSF-OAC-2148729](https://img.shields.io/badge/NSF_OAC-2148729-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2148729)
[![NSF-IIS-1912270](https://img.shields.io/badge/NSF_IIS-1912270-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1912270)
[![NSF-IIS-2148700](https://img.shields.io/badge/NSF_IIS-2148700-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2148700)
[![NSF-OAC-1916518](https://img.shields.io/badge/NSF_OAC-1916518-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1916518)

<sub>brainlife.io, which runs this App, is publicly funded by Wellcome, the U.S. National Institutes of Health and the U.S. National Science Foundation; acknowledging that support helps keep it running.</sub>

## License

See [LICENSE](LICENSE).
