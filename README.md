# Nuclear_Mechano_Response

This repository hosts the code and models developed for the paper titled  
**"Fibrillar adhesion dynamics govern the timescales of nuclear mechano-response via the vimentin 1 cytoskeleton"**  
currently available on BioRxiv: [https://www.biorxiv.org/content/10.1101/2023.11.08.566191v1](https://www.biorxiv.org/content/10.1101/2023.11.08.566191v1)

---

# Fibrillar Adhesions Govern Nuclear Mechano Response

Computational model (COMSOL Multiphysics) of how **fibrillar adhesions** anchor the **vimentin** network to regulate **nuclear deformation** and the **timescale of mechanotransduction**.  
The models reproduce key qualitative behaviors reported in the manuscript, including: (i) maintenance of a flattened nucleus after acute loss of contractility, (ii) delays in adaptation upon substrate changes, and (iii) vimentin-cage stress transmission during stretch.

---

## What’s in this repo

- **`COMSOL Models/`** – folder containing the COMSOL `.mph` model files used in the study  
  (e.g., baseline cell–nucleus model, softening/adaptation scenario, and stretch scenario).
- Refer to the **COMSOL Models/Instructions.md** or the following details on the specific model files and their implementation.  
> If you only need to run the models, you can **download the `.mph` files directly** from the folder—no cloning required.

---

# Instructions to use the files

The directory "COMSOL Models" contains three files, each representing a distinct simulation or study related to nuclear mechano-response. Below is an overview of the contents and their significance:

## List of Files

1. **Model_Sensitivity_Analysis**  
   This file contains the already completed Sensitivity Analysis model. It is implemented in a stationary state setting with the objective function as nuclear height.
2. **Nuclear_Vimentin_Interaction.mph**  
   The second file includes models for adhesion disassembly simulations.

3. **thickbot_stretch_v2_stationary.mph**  
   The third file contains the Stretch Simulation model.
## Significance

Each file is designed to assist users in reproducing, modifying, or extending various aspects of the nuclear mechano-response simulations. 

- The file **Model_Sensitivity_Analysis.mph** can be used to recreate the sensitivities presented in SI Table 2. 
- **Nuclear_Vimentin_Interaction.mph** is utilized for generating the results shown in Fig. 3m and animations. 
- The file **thickbot_stretch_v2_stationary.mph** is used for the stretch simulation depicted in Fig. 5i.
- Users should refer to the model definitions inside each file for specific simulation details, mesh settings, and solver configurations.

---
---

## Requirements

- **COMSOL Multiphysics**: v6.0 or later  
- **Module**: Solid Mechanics (required)  
- **OS**: Any OS supported by your COMSOL version (Windows/macOS/Linux)  
- **Recommended hardware**: Multi-core CPU; **16 GB RAM** (32 GB recommended for large sweeps)

---

## Download & Run 

1. **Download a model file**
   - Open the `COMSOL Models/` folder in this repository.
   - Click the `.mph` you want 
   - Click **Download** (or **Download raw**).

2. **Open in COMSOL**
   - Launch COMSOL Multiphysics.
   - **File → Open…** and select the downloaded `.mph`.

3. **Run the preconfigured study**
   - In **Model Builder**, expand **Study**.
   - Select the provided **Stationary** or **Time Dependent** study (as labeled in the file).
   - Click **Compute**.

4. **Inspect outputs**
   - **Derived Values / Global Evaluation** for nuclear height/area proxies and stress readouts.
   - **Results / Plots** for nuclear shape, vimentin-cage stresses, and substrate stress fields.
   - Export results via **Results → Export** (images/data) if needed.

---

## Typical scenarios

- **Time-dependent adhesion disassembly**: Use the time-dependent model and adjust the contractility and adhesion disassembly slope parameters to specify the desired decay rate. To compare scenarios with or without fibrillar adhesions, toggle the adhesion node on or off during simulation.
- **External stretch**: Open the stretch model and adjust the applied strain in the relevant boundary load; compute and quantify nuclear area change and stresses.

---

## Parameter notes

Key parameters are exposed in **Global Parameters**, including:
- **Nuclear mechanics**: bulk modulus `K_nuc`, shear modulus `mu_nuc`
- **Cell mechanics**: small-strain modulus `E_cell`; Mooney–Rivlin `C1`, `C2`
- **Active stress**: myosin contractility `rho`
- **Adhesion dissipation**: friction/viscosity constant `eta_d`

> The model is designed to capture **qualitative trends** across perturbations; parameters can be tuned for different cell types or treatments.

---

## Getting Started

1. Ensure COMSOL Multiphysics is installed on your system.
2. Open each `.mph` file in COMSOL to explore the geometry, physics settings, and results.
3. Modify the parameters as needed for your study or experimental setup.

If you have questions about the usage or setup of these files, please refer to the documentation or contact the repository maintainers.
## Troubleshooting

- **Slow/large runs**: Start with a coarser mesh; switch to PARDISO solver if available; reduce time span or number of sweep points.
- **Convergence issues**: Use parameter ramping/continuation; adjust solver tolerances; verify contact/BC definitions; initialize from a previously converged state.
- **Memory**: Refine only near contact zones and interfaces; limit 3D fields exported per time step.

---

## License

This project is released under the **GPL-3.0** license (see `LICENSE`).
