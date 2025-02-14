### 1. Paper title: Automatic differentiation in geophysical inverse problems, Geophysics, 2007
![image](https://github.com/user-attachments/assets/5c53ebfb-25ab-43aa-9d5f-3286d7989b52)

### 2. Problem to solve:

The computation of gradients/derivatives holds paramount significance across various scientific and engineering domains. From the perspective of sensitivity analysis in forward modeling  (Moresi et al. 2003, Komatitsch et al. 2005), gradients provide a quantitative measure of how model outputs respond to perturbations in input variables. This sensitivity information is crucial for understanding model behavior, optimizing model parameters, and assessing uncertainties. In the context of geophysical data inversion (Aster et al. 2005; Tarantola 2005), particularly when dealing with a large number of unknown parameters and highly nonlinear relationships (see Rawlinson & Sambridge 2003, for a recent review), the computation of gradients becomes exceedingly challenging. Traditional methods often struggle to balance accuracy and computational efficiency, especially when the complexity of the problem increases. Moreover, manual derivation of gradients is not only time-consuming but also prone to errors, especially when the underlying equations are intricate. The process of translating these derivations into engineering code and debugging them further exacerbates the problem. This approach lacks flexibility, as any changes in conditions necessitate a complete re-derivation of analytical or numerical solutions. Additionally, numerical methods for gradient computation require a delicate balance between accuracy and grid resolution, which can significantly impact computational costs. 

An ideal differential method would address these challenges by providing accurate and efficient gradient computation, and enabling efficient optimization in complex geophysical inversion problems. It should also streamline the process of code implementation and debugging, thereby reducing time and resource expenditure while enhancing flexibility and adaptability to changing conditions
   
### 3. Major contribution:
Automatic Differentiation technique can satisfy these three requirments, but to date (2007) AD seem to have made little impact on the Geosciences. The purpose of this paper is to help bring AD tools to the attention of the wider geoscience community, provide some useful references and illustrate its potential through a series of numerical experiments on common geoscience problems.

### 4. Theory and Experiment results:

Automatic differentiation (AD) is a method for computing the derivatives of functions, combining the advantages of symbolic differentiation (which is exact but potentially complex) and numerical differentiation (which is simple but prone to errors). Its objective is to efficiently and accurately calculate the derivatives of complex functions—such as gradients, Jacobian matrices, or Hessian matrices—without the need for manual derivation of these derivatives. A computer program, essentially a collection of instructions executed in sequence, can be viewed mathematically as a composite function. The key to automatic differentiation lies in the fact that the derivatives (or Jacobian matrices) of elementary functions can be computed exactly using simple rules. The derivatives of more complex functions are then obtained by applying the chain rule of differentiation.

![image](https://github.com/user-attachments/assets/7dcd9353-88c4-4103-a419-da9dc96c04b7)

1. Forward mode: It can be easier to implement and efficient on storage because once variables are no longer needed in the source code they can be discarded (overwritten) which reduces the storage needed to keep track of associated derivative variables. 

2. Reverse mode: With a single reverse sweep through the code list the derivatives of an output variable with respect to all input variables are available. The whole procedure must be repeated for every output variable, and hence a major advantage of the reverse mode is that the computational cost of evaluating the derivatives is proportional to the number of output variables m (multiplied by the length of the code list) rather than the number of input variables

![image](https://github.com/user-attachments/assets/8157b212-034e-4ce3-b40c-80a431dfc8fd)


1. Fig. 4(a) shows the ‘recalculate all’ strategy whereby the source code is restarted from the beginning each time the state changes
2. A second strategy is to store the complete values of all intermediate variables at every state, illustrated by Fig. 4(b).
3. A compromise between the two extremes is a checkpointing strategy, illustrated by Fig. 4(c). 

### 5. Lessons learnt:
Automatic Differentiation (AD) technique is an efficient and convenient method to calculate the gradient or derivatives relative to the input parameters, AD can be divided into two mode: forward mode and reverse mode. In the forward mode, we only want to require the value of output, which can drop out some intermediate variables. In the mode of reverse, we want to know the derivatives relative to the input parameters, which we need to restart to implement the forward mode and calculate the gradient of intermediate variables relative to the input parameters, which need more computational resources and cost. Here are some other method of reverse mode, like storing all and checkpointing stratege. 

In the future, how to balance the computational cost and memory management is an imporatant and significant problems in the scientific fields, especially in the non-linear invesion problem (e.g., Full Waveform Inversion). 
