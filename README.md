# Fibrillar Adhesions Govern Nuclear Mechano Response

Computational model (COMSOL Multiphysics) of how **fibrillar adhesions** anchor the **vimentin** network to regulate **nuclear deformation** and the **timescale of mechanotransduction**.  
The models reproduce key qualitative behaviors reported in the manuscript, including: (i) maintenance of a flattened nucleus after acute loss of contractility, (ii) delays in adaptation upon substrate softening set by fibrillar-adhesion disassembly, and (iii) protection against excessive nuclear strain during external stretch.

---

## What’s in this repo

- **`COMSOL Models/`** – folder containing the COMSOL `.mph` model files used in the study  
  (e.g., baseline cell–nucleus model, softening/adaptation scenario, and stretch scenario).

> If you only need to run the models, you can **download the `.mph` files directly** from the folder—no cloning required.

---

## Requirements

- **COMSOL Multiphysics**: v6.0 or later  
- **Module**: Structural Mechanics (required)  
- **OS**: Any OS supported by your COMSOL version (Windows/macOS/Linux)  
- **Recommended hardware**: Multi-core CPU; **16 GB RAM** (32 GB recommended for large sweeps)

---

## Download & Run 

1. **Download a model file**
   - Open the `COMSOL Models/` folder in this repository.
   - Click the `.mph` you want (e.g., baseline or softening/stretch variant).
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

- **Acute loss of contractility**: Use the baseline model and set the contractility parameter (`rho`) to zero (or use the preconfigured “loss of contractility” study) to observe nuclear rebound with/without vimentin anchoring.
- **Substrate softening / adaptation timescale**: Open the softening/adaptation model and run the **Time Dependent** study where substrate modulus decreases at a specified time; examine the lag before nuclear readout decays.
- **External stretch**: Open the stretch model and adjust the applied strain (e.g., 10–13%) in the relevant boundary load; compute and quantify nuclear area change and stresses.

---

## Parameter notes

Key parameters are exposed in **Global Parameters**, including:
- **Nuclear mechanics**: bulk modulus `K_nuc`, shear modulus `mu_nuc`
- **Cell mechanics**: small-strain modulus `E_cell`; Mooney–Rivlin `C1`, `C2`
- **Active stress**: myosin contractility `rho`
- **Adhesion dissipation**: friction/viscosity constant `eta_d`

> The model is designed to capture **qualitative trends** across perturbations; parameters can be tuned for different cell types or treatments.

---

## Troubleshooting

- **Slow/large runs**: Start with a coarser mesh; switch to PARDISO solver if available; reduce time span or number of sweep points.
- **Convergence issues**: Use parameter ramping/continuation; adjust solver tolerances; verify contact/BC definitions; initialize from a previously converged state.
- **Memory**: Refine only near contact zones and interfaces; limit 3D fields exported per time step.

---

---

## License

This project is released under the **GPL-3.0** license (see `LICENSE`).
