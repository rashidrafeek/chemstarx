# Instructions

## Step-1: Set-up 

- Open terminal
- Run `conda activate chemstarx`

## Step-2: Reactant optimization

- Open Avogadro
- Build Methyliodide molecule
- Go to `Build > Cartesian Editor > Sort by > Element`
- Generate input for geometry optimization using Avogadro NWCHem template 
	Extensions > NWChem
- Add required blocks of Basis sets, Iodine basis and XYZ output from "utilites" file
- Run `mpirun -np 4 nwchem CH3I_GS.nw > CH3I_GS.nwo` in terminal

## Step-3: Product optimization

- Open Avogadro
- Build Methylchloride molecule
- Go to `Build > Cartesian Editor > Sort by > Element` 
- Generate input for geometry optimization using Avogadro NWCHem template
	Extensions > NWChem
- Add required blocks of Basis sets and XYZ output from "utilites" file 
- Run `mpirun -np 4 nwchem CH3Cl_GS.nw > CH3Cl_GS.nwo` in terminal

## Step-4: PES preliminary

- Open Avogadro
- Build CH3I + Cl- molecule
- Go to `Build > Cartersian Editor > Sort by > Element` 
- Generate input for geometry optimization using Avogadro NWCHem template
- Set C-Cl distance to 3.000 angstroms 
- Add required blocks of Basis sets, Iodine basis, XYZ output and geometric constraints from "utilites" file
- Run `mpirun -np 4 nwchem CH3I_Cl.nw > CH3I_Cl.nwo` in terminal

- Open Avogadro
- Build CH3Cl + I- molecule
- Go to `Build > Cartersian Editor > Sort by > Element`
- Generate input for geometry optimization using Avogadro NWCHem template
- Set C-I distance to 3.000 angstroms
- Add required blocks of Basis sets, Iodine basis, XYZ output and geometric constraints from "utilites" file
- Run `mpirun -np 4 nwchem CH3I_Cl.nw > CH3I_Cl.nwo` in terminal

## Step-5: LIIC Calculation

- Open the latest XYZ file for CH3I_Cl
- Build Menu > Cartesian Editor > Sort bt "Element" 
- Copy Python block for LIIC from "utilities"
- Fill in appropirate values for x0, y0, xmax, xmin and npts
- mpirun -np 4 nwchem CH3I_Cl_PES1.nw > CH3I_Cl_PES1.nwo 

- Open the latest XYZ file for CH3Cl_I
- Build Menu > Cartesian Editor > Sort bt "Element" 
- Copy Python block for LIIC from "utilities"
- Fill in appropirate values for x0, y0, xmax, xmin and npts
- mpirun -np 4 nwchem CH3Cl_I_PES1.nw > CH3Cl_I_PES1.nwo

## Step-6: 2D PES Calculation 

- Open the latest XYZ file for CH3I_Cl
- Build Menu > Cartesian Editor > Sort bt "Element" 
- Copy Python block for 2D PES from "utilities"
- Fill in appropirate values for x0, y0, xmax, xmin and npts
- mpirun -np 4 nwchem CH3I_Cl_PES2.nw > CH3I_Cl_PES2.nwo 

- Open the latest XYZ file for CH3Cl_I
- Build Menu > Cartesian Editor > Sort bt "Element" 
- Copy Python block for 2D PES from "utilities"
- Fill in appropirate values for x0, y0, xmax, xmin and npts
- mpirun -np 4 nwchem CH3Cl_I_PES2.nw > CH3Cl_I_PES2.nwo
