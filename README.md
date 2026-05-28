# Inter-IIT-LAT-Aerospace-
Inter IIT Tech Meet solution by Team IIT BHU for the L&amp;T Aerospace problem statement, including design methodology, simulations, analysis, and final implementation.

# 1. Airfoils/

This folder contains all ANSYS Workbench CFD analyses for the selected airfoils. The objective of these simulations is to study the aerodynamic behavior near the stalling angle of attack, focusing on flow separation, pressure distribution, velocity contours, and lift–drag characteristics. These studies evaluate flow separation, pressure distribution, lift–drag performance, and mesh independence for low‑Re, high‑lift applications.

The **Additional Files/** folder contains the ANSYS Workbench project files and relevant setup data for CFD analyses performed on multiple airfoil and wing configurations.
---

## 📁 E423/

Contains CFD studies for the E423 airfoil.

- `E423_analysis.wbpj`
  Complete Workbench project with domain definition, meshing strategy, solver settings, and solution setup.

- `E423_analysis_files/`
  ANSYS-generated support files required to run or post‑process the project.

---

## 📁 S1223/

High‑lift reference airfoil used for comparison with S1210.
- `S1223_analysis.wbpj`
  Complete Workbench project with domain definition, meshing strategy, solver settings, and solution setup.

- `S1223_analysis_files/`
  ANSYS-generated support files required to run or post‑process the project.

---

## 📁 S1210/

Primary airfoil used for both takeoff and cruise wing configurations.
### 📁 Takeoff/
  Includes:
  - `S1210_takeoff_analysis.wbpj`
    Complete Workbench project with domain definition, meshing strategy, solver settings, and solution setup.
  - `S1210_takeoff_analysis_files/`
    ANSYS-generated support files required to run or post‑process the project.

### 📁 Cruise/
  Includes:
  - `S1210_cruise_analysis.wbpj`
    Complete Workbench project with domain definition, meshing strategy, solver settings, and solution setup.
  - `S1210_cruise_analysis_files/`
    ANSYS-generated support files required to run or post‑process the project.

---

## 📁 GCI_Studies/

Grid Convergence Index documentation for S1210

These studies justify mesh independence and the transition from structured/block meshes to unstructured meshes suitable for flap geometries.
- `GC_2D.wbpj`
- `GC_2D_analysis_files/`

---

# 2. Flaps/

This folder contains all flap‑related utilities, CAD geometries, and CFD simulations, organized into a pipeline that starts with 2D parametric flap studies and progresses to validated 3D wing–flap configurations for the final STOL design.​ We tstarted withsome simulations varying flap parameters and then obtained using the code. 

---

## 📁 Flap_Parameter_Code/

Python scripts for generating optimum flap geometries.

`flap_optimization.ipynb`

---

## 📁 2D_CFD/

CFD analysis for various 2D flap configurations, used to select the optimal geometry and deflection for 3D analysis.

### 📁 Cruise/
- `S1210_cruise_2D.wbpj`: The simulation files for the wing with flaps at cruise
- `S1210_cruise_2D_files/` (Contains ANSYS support files for each iteration X)
### 📁 Takeoff/
- `S1210_takeoff_2D.wbpj`: The simulation files for the wing with flaps at takeoff
- `S1210_taekoff_2D_files/` (Contains ANSYS support files for each iteration X)

Includes:

- Lift and drag studies with varying flap parameters (namely gap, overlap and deflection).
- $C_L$ enhancement relative to the S1210 baseline for parameter sweep.
- Assessment of maximum lift and associated drag penalties.

---
# 3. Wing/

This folder contains 3D wing analyses, mathematical models, and the final integrated wing–flap simulations for both takeoff and cruise.

---
## 📁 Math_Model/

Contains the mathematical model for wing parameters selection, which would narrow down the choice for high-fidelity CFD analysis

Files:
- `wing_design.ipynb` – Code to predict best wing design parameters
- `wing_paramteric_results_Re1e5.xlsx` – Results for varying wing parameters at takeoff. Code output is stored in sheet1. Sheet2 stores the validation against XFLR5
- `wing_paramteric_results_Re5e5.csv` – Results for varying wing parameters at cruise.

### 📁 Datasets
Contains the input datasets for the code.
- `xf-s1210-il-100000.csv` - Contains the polars for S1210 at Re = 100000
- `xf-s1210-il-500000.csv` - Contains the polars for S1210 at Re = 500000

**Required Python libraries:**
`numpy`, `pandas`, `scipy`, `matplotlib`

Includes:

- Predicting lift and drag for varying wing parameters.
- $C_L$ enhancement by choosingthe optimum geometry
- Assessment of wing performance at both takeoff and cruise conditions

---
## 📁 Geometry/

Contains the CAD files for the domain and geoemtries. Use these if you want to run simulations separately.

### 📁 Takeoff/
- `wing_takeoff_domain.step` – Use this as domain for ansys geometry
- `wing_takeoff.step` – Wing with flaps deployed geometry

### 📁 Cruise/
- `wing_cruise_domain.step` – Use this as domain for ansys geometry
- `wing_cruise.step` – Wing with flaps retracted geometry


## 📁 Wing+Flaps_Integrated/

3D CFD analyses of the wing with flaps in both deployed (takeoff) and retracted (cruise) configurations, using the geometry defined in **Flaps/Geometry/**.

### 📁 Takeoff/
- `wing with flap without thrusters.wbpj`: Simulation for integrated wing+flpas system at takeoff conditions
- `wing with flap without thrusters_files/`: Support files for ANSYS simulation. Ensure that this remains in the same directory.

### 📁 Cruise/
- `1210_cruise_3D.wbpj`: Simulation for integrated wing+flpas system at takeoff conditions
- `1210_cruise_3D_files/`

---

## 📁 3D Mesh Independence/

Grid Convergence Index and mesh‑sensitivity studies for the 3D wing and wing+flap configurations, supporting numerical reliability in the 3D simulations.
### 📁 7mm wake region_14mm outer region/
- `new wing 7_14 mezh independence.wbpj`: ANSYS workbench simuation
- `new wing 7_14 mezh independence_files/`
### 📁 8mm wake region_14mm outer region/
- `new wing 8_16 mezh independence.wbpj`: ANSYS workbench simuation
- `new wing 8_16 mezh independence_files/`
### 📁 9mm wake region_14mm outer region/
- `new wing 9_18 mezh independence.wbpj`: ANSYS workbench simuation
- `new wing 9_18 mezh independence_files/`


---


# 4. Structural_Analysis/

This section documents structural integrity checks for the wing and associated components using FEA.

---

## 📁 Wing_FEA/

- `FEA_final.wbpj`
  Complete Workbench project with domain definition, meshing strategy, solver settings, and solution setup.

- `FEA_final_files/`
  ANSYS-generated support files required to run or post‑process the project.

Contains:

- ANSYS Mechanical structural model.
- Mesh setup and refinement details.
- Load and boundary condition definitions (aerodynamic pressure, thruster mounts, supports).
- Von Mises stress and deformation plots.
- Factor of safety estimates and tip‑deflection values.

All setup and results are stored in a single ANSYS Mechanical project for easy reruns.

---

# 5. Thruster/

This folder investigates propeller performance, slipstream characteristics, and thruster–wing interaction.

## 📁 Thruster_Velocity_Validation/

Compares momentum‑theory predictions with CFD (ANSYS Fluent) for thruster exit velocity and thrust, used to validate the numerical setup.
Compares momentum-theory predictions with CFD (ANSYS Fluent).
- `Velocity_Validation.wbpj`
- `Velocity_Validation_files`

---

## 📁 Propeller_Count_Study/

Parametric study of different propeller counts of the EDF. Using this, the optimum number of propellers was chosen.
### 📁 2 thrustrers iteration/
- `2dizkfluent.wbpj`: Simulation for integrated wing+flpas system at takeoff conditions
- `2dizkfluent_files/`: Support files for ANSYS simulation. Ensure that this remains in the same directory.

### 📁 3 thrustrers iteration/
- `3_propellers.wbpj`: Simulation for integrated wing+flpas system at takeoff conditions
- `3_propellers_files/`

### 📁 5 thrustrers iteration/
- `5dizkfluent.wbpj`: Simulation for integrated wing+flpas system at takeoff conditions
- `5dizkfluent_files/`: Support files for ANSYS simulation. Ensure that this remains in the same directory.

- 2, 3, and 5‑propeller configurations.(NOTE: These counts refer to the number of propellers on half-wing)
- Total thrust and power requirements.
- Slipstream width and qualitative coverage of the wing.
- Overall propulsive efficiency.


## 📁 Mounting_Position_Analysis/

### 📁OpenVSP/
- `iteration_0.05_0.01`: Wing with 6 propellers 70mm each at position x=-0.05m and z=0.01m.
- `iteration_0.05_0.02`: Wing with 6 propellers 70mm each at position x=-0.05m and z=0.02m.
- `iteration_0.05_0.03`: Wing with 6 propellers 70mm each at position x=-0.05m and z=0.03m.

- Lift and drag analysis by varying vertical position of thrusters in OpenVSP


### 📁ANSYS/
High-Fidelity CFD analysis of thruster placement relative to the wing and flaps to optimize Coandă and USB interaction.

- `vertical_position_analysis_0.01,0.02,0.03m.wbpj`
- `vertical_position_analysis_0.01,0.02,0.03m_files`

- Lift and drag analysis by varyng vertical position of thrusters in OpenVSP
- Finalizing thruster position

---
# 6. PINNs for CFD
Full code for using PINNs to reduce the CFD computtin time for 2D analyses by taking corase input as mesh and giving the output corresponding to finer mesh (acuurate output). In addition the files have been provided, which is to be used as input for the code.

## 📁 Code/
- `PINN_Mesh_Refinement.ipynb`: Code for mesh refinement 

## 📁 Dataset/
- `S1210_10mm.csv `: Nodal data at 10mm mesh size obtained from ANSYS simulation
- `S1210_boundary_data.csv`: Data of boundary of airfoil

- Libraries: `numpy, pandas, scipy, matplotlib, os, sklearn, warnings, math, time, torch`

# 7. Final_Combined_Results/

Contains the complete aerodynamic evaluation of the integrated wing–flaps–thrusters system for both takeoff and cruise.

## 📁 Geometry/
Final integrated model geometry.
### 📁 CAD_Files/
- CAD assembly of the full wing, flaps, and thrusters.
- `wing_final.step`

## 📁 Takeoff/
Full‑system simulations for takeoff ($C_L$, $C_D$, stall margin).
- `takeoff_final_iteraton.wbpj`: This stores all iterations for mutltiple AoA, out of which the simulations for 3 AoA is the final setup.
- `takeoff_final_iteraton`: Support files for the ANSYS workbench.

Includes:
- Final takeoff $C_L, $C_D$, lift force.
- Lift enhancement strategies and results.
- Overall performance at takeoff.

## 📁 Cruise/
Full-system simulations for cruise ($C_L/C_D$ efficiency).

- `Cruise_Final.wbpj`
- `Cruise_Final_files`
Includes:
- Final cruise $C_L/C_D$.
- Drag‑reduction strategies and results.
- Overall performance at cruise.

---

# ▶ How to Run ANSYS Workbench Files


## Opening the Project

1. Launch **ANSYS Workbench (2025 R1 or later)**.
2. Go to **File → Open**
3. Select the desired .wbpj file.
4. Ensure the corresponding **_analysis_files/** folder is located in the same directory.
5. Allow Workbench to update or relink components if prompted.

---

## Updating Components

### Geometry

- Confirm that geometry loads without errors.
- Regenerate if changes are detected or if warnings appear.

### Mesh

- Verify named selections and mesh controls.
- Regenerate mesh if any error occurs.

### Setup (Fluent)

- Open Fluent from the Setup cell.
- Verify:
  - Under reference values Compute from inlet is selected.
  - Inlet velocity is correct (takeoff = 20 m/s or cruise =  80 m/s, also ensure the velocity components at that AoA are correct).
  - Fluid properties and operating conditions.
  - Report definitions (ensure correct vector components for lift and drag are given)


---

## Running the Simulation

- Use **Run Calculation** in Fluent.
- Set number of iterations = 1000 and monitor residuals and force coefficients.
- Ensure convergence based on steady residuals and stable $C_L$ and $C_D$.
- Compute results once solution converges.

---

## Viewing Results

Use Fluent or CFD post‑processing tools to generate:

- Pressure and velocity contour plots
- Velocity vectors and streamlines
- $C_L$, $C_D$, Lift force and drag force

---

# ▶ Running Python Codes

### Requirements# ▶ Running Python Codes

- `Python 3.x`
- Libraries: `numpy, pandas, scipy, matplotlib, os, sklearn, warnings, math, time, torch`

### Instructions

1. Open `flap_optimization.ipynb` and `wing_design.ipynb` in **Jupyter Notebook** or **GoogleColab**.
2. Install missing libraries using pip or conda if required.
3. Run the notebook cells in order to:
   - Load base airfoil and flap data.
   - Generate candidate wing+flap geometries.
   - Export geometry and performance summaries to .csv for use in CFD and structural models.

# ▶ Opening CAD files

### Requirements
1. Use **Solidworks 2023 or later**.

