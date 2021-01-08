# SSAsimpleM
Model for 1D marine ice sheet evolution (SSA approximation) in MATLAB, using numerical approach from Schoof 2007

This model is a 1D flowline of ice sheet flow, where equations for ice velocity, ice thickness, and grounding line position are simultaneously solved using an implicit discretization in time and a finite difference scheme in space. All variables are scaled in space so that the grounding line is always at a node, and to ensure high resolution near the grounding line for an accurate solution. The spatial domain is further subdivided into a coarse grid upstream of the grounding line and a refined grid near the grounding line. This numerical scheme has been benchmarked against the asymtpotic grounding line flux formulate in Schoof (2007) and converges well in resolution.

This scheme can be set to transient or steady-state mode, where the solver solves for ice sheet evolution in time (transient) or the nearest steady-state of the system. Please be aware though, that the steady-state mode requires an initial guess for the solution, and for strongly nonlinear or non-smooth systems will have difficulty converging on a solution.

The "M" in the repository name stands for MATLAB. The script is completely self-contained and requires no other functions beyond those built into MATLAB (c. 2020, but nothing in it is sufficiently fancy that it probably is back compatible for about the last decade of MATLAB). To find the solution of the system of equations, this script uses fsolve, the MATLAB built-in solver for nonlinear systems of equations. fsolve use a numerical finite difference scheme to find the Jacobian of the system of equations, which is somewhat slower than analytic Jacobian schemes (see SSAsimpleJ for an implementation in Julia using automated differentiation). Numerical Jacobian schemes may also be prone to inaccuracies near non-smooth system variations (i.e. jagged bedrock topography).
