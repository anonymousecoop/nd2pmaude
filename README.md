# Actors2PMaude

We have implemented in Maude using Maude's meta-level facilities the P and the Sim transformations and have also integrated parallelized PVeStA statistical model checker into a single tool.

The tool consists of three components:

- The Actors2PMaude component implements the P transformation and includes the probability distribution library. 
- The PMaude2Sim component applies the Sim transformation to the resulting module, and also includes an extensible sampling library. 
- The SMC component performs the SMC analysis with simulations obtained by executing the simulation model together with the associated initial state.  

Using the tool: 

Step 1. The Actors2PMaude tool is a client-server-based parallelization of SMC analysis. The user must first run the following script at the client side to launch each server:

  ./launch.sh serverlist
  
where serverlist is the file containing a list of available servers for running simulations. 

Step 2. The user then starts the client by running the following script: 

  ./run.sh -smc mode -pt gasys init distr -pv quatex confidence size serverlist
  
Turning mode on leads to a "one-button" SMC analysis where the QuaTEx formula can be defined without investigating the intermediate modules generated by the P or Sim transformation; otherwise, i.e., to see the P- and Sim-generated modules, mode should be off. gasys, init, and distr refer to the files containing the GARwTh, the initial state, and $\Pi$, respectively. The files quatex and serverlist contain the QuaTEx formula and the server list, and confidence and size denote the confidence level and size parameters, respectively.  
