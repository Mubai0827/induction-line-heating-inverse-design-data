![Induction line-heating inverse design banner](assets/banner.svg)

# Induction line-heating inverse design for steel plates

<p align="center">
  <strong>Point-cloud conditions · Full-field deformation · Generative process planning</strong>
</p>

> [!IMPORTANT]
> **Data status: one authentic example case is available.** The complete dataset and model code are **not** deposited here. The two illustrations on this page are explanatory schematics, not finite-element outputs. Please do not describe this repository as a release of all data supporting the paper.

## Research at a glance

Induction line heating helps form curved steel plates for shipbuilding. The inverse problem is to find heating settings that produce a desired three-dimensional plate deformation. Because different processes can lead to similar deformations, a single deterministic answer may miss useful alternatives.

The associated manuscript, **“Generative inverse design of induction line-heating processes for steel plates from three-dimensional displacement fields,”** studies this problem with point-cloud representations and a conditional variational autoencoder (CVAE).

![Schematic of the inverse-design workflow](assets/workflow.svg)

| Stage | Role in the study |
| --- | --- |
| **Condition** | Initial plate point cloud, target pointwise 3D displacement field, and plate geometry |
| **Generate** | A hierarchical decoder proposes heating-line count, continuous positions, and temperature–speed classes |
| **Screen** | A frozen forward surrogate estimates full-field deformation and ranks candidate processes by target-field error |
| **Verify** | Selected alternatives are checked independently with finite-element simulations |

The manuscript reports **22,620 valid finite-element cases**, an experiment that generates **20 candidates per target**, and independent finite-element checks of **75 alternative processes**. These numbers describe the study, **not** the contents of this repository.

## Available example

A single real finite-element case is available at **[data/example_case_300x300x08_1line/A1X0030X0000X0000a00](data/example_case_300x300x08_1line/A1X0030X0000X0000a00)**.

It contains 3,721 point samples and the corresponding initial point features, three-dimensional displacement components, plate/process parameters, and documented metadata. See the [example-case README](data/example_case_300x300x08_1line/A1X0030X0000X0000a00/README.md) for column definitions and a loading example. The numerical arrays are unchanged from the source case; a local absolute path was removed from the public metadata.

This **one-case subset cannot reproduce the manuscript's training, test-set comparisons, or aggregate validation results**. The manuscript currently states that the datasets generated and analyzed during the study are available from the corresponding author on reasonable request. If this repository is cited in a submission form, the manuscript's data availability statement should be updated to identify the public *example* separately from the complete data available on request.

No dataset DOI has been assigned. Public visibility does not by itself grant a reuse license; any reuse terms require author approval.

## Repository map

```text
assets/  — explanatory SVG illustrations (not simulation outputs)
data/
  example_case_300x300x08_1line/
    A1X0030X0000X0000a00/
      point_features.npy
      disp.npy
      global_features.npy
      meta.json
      README.md
```
