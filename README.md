[![Abcdspec-compliant](https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg)](https://github.com/brain-life/abcd-spec)
<!-- [![Run on Brainlife.io](https://img.shields.io/badge/Brainlife-bl.app.1-blue.svg)](https://doi.org/10.25663/brainlife.app.435) -->

# Description

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Computes binary and weighted structural-connectivity predictors (path length, communicability, cosine distance, mean first passage time, matching index, search information, path transitivity) and how well each predicts functional connectivity per brain region.**

Derives 14 network predictors from a structural connectivity matrix and, for every region, correlates each predictor with that region's functional connectivity profile, saving the squared correlations (r^2) per region and predictor. Use it to study local structure-function coupling. The code reads two connectivity matrices (structural first, functional second) from the conmat input although the input is registered as a single matrix, and it writes a CSV (output/csv/rsq.csv) although the output is registered as a PDF report.

| | |
|---|---|
| 📥 **Inputs** | `neuro/conmat` |
| 📤 **Outputs** | `report/pdf` |
| 🐳 **Container** | `filsilva/cxnetwork:0.2.0` |
| ⚙️ **Resources** | 1 CPUs · 6 GB memory · 1 h walltime |
| 🔗 **Run it** | [doi.org/10.25663/brainlife.app.646](https://doi.org/10.25663/brainlife.app.646) |

#### 📥 Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `conmat` | `neuro/conmat` | yes |  |

#### 📤 Outputs

| Output | Datatype | Description |
|---|---|---|
| `output` | `report/pdf` |  |

<details>
<summary><b>⚙️ Parameters</b> (3)</summary>

| Parameter | Type | Default | Description |
|---|---|---|---|
| `gammavals` | number | `0.5` | convert edge weight to cost |
| `predictors` | enum | `all` | Which predictor to evaluate; 'all' evaluates all 14 binary and weighted predictors. Options: `all`, `PLbin`, `Gbin`, `Cosbin`, `mfptbin`, `MIbin`, `SIbin`, `PTbin`, `Gwei`, `Coswei`, `mfptwei`, `MIwei`, `SIwei`, `PTwei`, `PLwei`. |
| `remove nodes` | enum | `false` | remove isolated nodes (row/columns with all zero values) Options: `true`, `false`. |

</details>

📚 **References used by this App:**
- Esfahlani FZ, Faskowitz J, Slack J, Misic B, Betzel R. Local structure-function relationships in human brain networks across the human lifespan. bioRxiv (2021).

<!-- brainlife-app:end -->

Brainlife App for generating a set of predictors from structural connectivity matrix. 
### Authors
- [Farnaz Zamani Esfahlani]

<!-- ### Contributors
- [Richard F. Betzel]
- [Franco Pestilli]
- [Filipi Nascimento Silva]

### Funding Acknowledgement
brainlife.io is publicly funded and for the sustainability of the project it is helpful to Acknowledge the use of the platform. We kindly ask that you acknowledge the funding below in your publications and code reusing this code.-->

[![NSF-BCS-1734853](https://img.shields.io/badge/NSF_BCS-1734853-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1734853)
[![NSF-BCS-1636893](https://img.shields.io/badge/NSF_BCS-1636893-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1636893)
[![NSF-ACI-1916518](https://img.shields.io/badge/NSF_ACI-1916518-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1916518)
[![NSF-IIS-1912270](https://img.shields.io/badge/NSF_IIS-1912270-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1912270)
[![NIH-NIBIB-R01EB029272](https://img.shields.io/badge/NIH_NIBIB-R01EB029272-green.svg)](https://grantome.com/grant/NIH/R01-EB029272-01)

### Citations
1. Esfahlani, F. Z., Faskowitz, J., Slack, J., Misic, B., & Betzel, R. (2021). Local structure-function relationships in human brain networks across the human lifespan. bioRxiv. 


<!-- 3. Costa, L. da F., Francisco A. Rodrigues, Gonzalo Travieso, and Paulino Ribeiro Villas Boas. "Characterization of complex networks: A survey of measurements." Advances in physics 56, no. 1 (2007): 167-242.[https://doi.org/10.1080/00018730601170527](https://doi.org/10.1080/00018730601170527) -->

## Running the App 

<!-- ### On Brainlife.io

You can submit this App online at [https://doi.org/10.25663/brainlife.app.435](https://doi.org/10.25663/brainlife.app.435) via the "Execute" tab. -->

### Running Locally (on your machine)
Singularity is required to run the package locally.

1. git clone this repo.

```bash
git clone <repository URL>
cd <repository PATH>
```

2. Inside the cloned directory, edit `config-sample.json` with your data or use the provided data.

3. Rename `config-sample.json` to `config.json` .

```bash
mv config-sample.json config.json
```

4. Launch the App by executing `main`

```bash
./main
```

### Sample Datasets

A sample dataset is provided in folder `data` and `config-sample.json`

## Output

The output is a csv file includig the r-squared values for every brain region and predictor. 

### Dependencies

This App only requires [singularity](https://www.sylabs.io/singularity/) to run. If you don't have singularity, you will need to install the python packages defined in `environment.yml`, then you can run the code directly from python using:  

```bash
./main.py config.json
```

