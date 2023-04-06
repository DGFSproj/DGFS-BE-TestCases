# 1 Dimensional Normal Shock Flow Case
This test case involves a one-dimensional normal shock problem. Shock waves are an important concept in the field of aerospace engineering and play an important role in the development of supersonic engines, turbomachinery, supersonic vehicle surfaces, rockets, missiles, and reentry vehivles. This DGFS of the Boltzmann equation provides clear allignment with the DSMC solution. 

## Test Case Characteristics 
In this test case, we use Helium as the working gas. There are three different file endings used: .ini, .geo, and .msh. 
### Input File 
The .ini file includes physical and numerical parameters for this test case. Starting from the top of the file, the section **[non-dim]** includes the nondimensional units of temperature (T0), shock thickness (H0), and density (rho0). The molecular weight of the working gass (MW) is also included. The molecular model parameters are defined in the **[scattering-model]** section. The solver uses a VHS model and includes the viscosity index (omega), reference diameter (dRef), and reference temeprature (Tref) Various other gas model properties can be found in the Appendix of  [[1]](#1). The order of the solver is given in the section **[solver]**. For this case, we use a DG order of 2. The time intergation parameters are inlcuded in the section **[solver-time-integrator]**. The type of time solver is given as dgfs-euler. Further, the start time (tstart), end time (tend), and time difference (dt) are given. Note that tend and dt are nondimensionalized units. The initial conditions are given in the section **[soln-ics]** as linear models of density (rho), temperature (T0), x-velocity (ux), y-velocity (uy), and z-velocity (uz). The last two sections **[soln-bcs-left]** and **[soln-bcs-right]** give the upstream and downstream boundary conditions using the same parameters as the above initial conditions section. 

## Flow Visualization 
<img src="./resources/DGFS_DSMC_normal_shock.png" alt="NormalShock_Comparison" width="400"/>
## References
<a id="1">[1]</a> 
Bird, Graeme Austin. Molecular Gas Dynamics. Oxford: Clarendon Press, 1976. Print.

