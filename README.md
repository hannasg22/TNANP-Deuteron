# DEUTERON

## Goal of the code

Briefly explained, this code is provided to solve specifically the deuteron equations and get its eigenfunctions and eigenvalues.

In order to find the results, a particular model for the potentials is implemented. However, another option could be applied, making use of the user's preferred election.

## Theory

With the aim of better understanding what it is done in this code, let us introduce the main theoretical concepts.

### Main idea

The deuteron is the **only bound state of two nucleons** and its bound is weak, therefore it only exists in the ground state. It is formed by one proton and one neutron and the nuclear force between them has the next main properties: attractive (to form the bound state), short range (of order of $\sim 1fm$ ) and non-central (it has a tensor component). 

All these assumptions have been made through the obtained experimental data. Furthermore, the potential describing the interaction between both particles has been contructed more precisely to fit the actual results. It can be widely analysed and it will show many different components. We instead will focus on the **two main quantities**:
- Central potential $V_C$
- Tensorial potential $V_T$

Both can also be described by diverse models. One option (the one we will use) is to define them through Yukawa potential wells:

$$ V=V_C(r)+V_T(r)\hat{S}=-47\frac{exp(r/1.18)}{r/1.18}-24\frac{exp(r/1.7)}{r/1.7}\hat{S}
$$

where $\hat{S}=\hat{S}_{12}$ is the tensor operator. The strength of the potentials is defined in MeV and the distance r in fm. This specific choice has been made to fit the model exposed in the [Gezerlis book](https://numphyspy.org) _Numerical Methods in Physics with Python_.

Now, let us derive the form of the Hamiltonian using some of the deuteron's properties. The deuteron has total isospin $T=0$ and spin parity $J^{\pi}=1^+$. As $s_p=s_n=1/2$, the total spin could in principle be $S=1,0$. At the same time, parity conservation imposes some rules for the quantum number for the orbital angular momentum $L$ (together with $J-1 < L < J+1$): since parity follows rule $\pi=(-1)^l=+1$, only $L=0$ (S-wave) and $L=2$ (D-wave) are allowed. This means that the ground state of deuteron is a mixture of these two wavefunctions (which are connected through the tensor interaction). At this point, due to the asymmetry of the whole wavefunction in a system of two fermions, we have $S=1$ for the total spin.

These results lead us from the total Hamiltonian

$$ H=-\frac{\hbar^2}{M}\frac{1}{r}\frac{d^2}{dr^2}r+\frac{\hbar^2}{M}\frac{L(L+1)}{r^2}+V_C(r)+V_T(r)S_{12}
$$

into two radial equations describing the system, which after inserting the properties and quantum numbers of the deuteron have the next form:

$$ [\frac{\hbar^2}{M}\frac{d^2}{dr^2}+E-V_C(r)]u_s=\sqrt{8}V_T(r)u_d
$$

$$ [\frac{\hbar^2}{M}(\frac{d^2}{dr^2}-\frac{6}{r^2})+E+2V_T(r)-V_C(r)]u_d=\sqrt{8}V_T(r)u_s
$$

These are exactly the equations that our code will try to solve! So, we will **get the two wavefunctions $u_s$ and $u_d$ and the energy eigenvalue** (which, by experimental data, we know it is: $E_B=-2.225 MeV$).

Also, we must take into account the initial and boundary conditions we expect this kind of system to follow:

$$u_s(0)=u_d(0)=0, \hspace{0.5cm} u_s(\infty)=u_d(\infty)=0
$$

### Further details
