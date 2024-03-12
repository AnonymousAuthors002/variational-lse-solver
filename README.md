# Comprehensive Library of Variational LSE Solvers

This repo contains the code for the PennyLane-based `variational-lse-solver` library introduced in 
"Comprehensive Library of Variational LSE Solvers", Anonymous Authors (2024).

## Setup and Installation

The library requires an installation of `python 3.12`, and following libraries:
- `pennylane~=0.34`
- `torch~=2.1.2`
- `tqdm~=4.66.2`

We recommend setting up a conda environment:

```
conda create --name ENV_NAME python=3.12
conda activate ENV_NAME
```

The package `variational-lse-solver` can be installed locally via:
```
cd variational-lse-solver
pip install -e .
```

## Usage and Reproduction of Results

Information on how to use the different modalities of the libraries are described in the documentation.
Additionally, we provide to usage examples.

#### Reproduce Paper Results

To reproduce the results depicted in the paper, one can run

```
python examples/reproduce_result.py --steps 50 --mode='unitary'
```
Keep in mind, that the reported results were averaged over 100 random initializations. 
In order to use the local cost function, just add the `--local` flag. 
It is also possible to use the matrix decomposition modes `unitary` and `circuit`.
Running the script wil print the solution found with the variational LSE solver, as well as the classically validated solution.

#### Solve Random LSE

To solve a randomly generated LSE with a system matrix of size `2^size x 2^size`, one can run
```
python examples/test_random_system.py --size 3 --threshold 1e-4
```
In order to use the local cost function, just add the `--local` flag. 
To increase the accuracy of the solution, reduce the value of `threshold`.
The implementation by default uses the `direct` mode, i.e. no matrix decomposition is performed.
Running the script wil print the solution found with the variational LSE solver, as well as the classically validated solution.

## Acknowledgements

The `variational-lse-solver` library is mostly based on the techniques introduced in
["Variational Quantum Linear Solver", C. Bravo-Prieto et al., Quantum 7, 1188 (2023)](https://quantum-journal.org/papers/q-2023-11-22-1188/).

The concept of using dynamically growing circuits is inspired by
["Variational quantum linear solver with a dynamic ansatz", H. Patil et al., Phys. Rev. A 105, 012423 (2022)](https://journals.aps.org/pra/abstract/10.1103/PhysRevA.105.012423)

There are some alternative implementations of subroutines provided by `varaitional-lse-solver` in the PennyLane Demos:
- https://pennylane.ai/qml/demos/tutorial_vqls/
- https://pennylane.ai/qml/demos/tutorial_coherent_vqls/

However, those realisations contain several hard-coded parts and can not be used for arbitrary problems out of the box.
Furthermore, we identified some small inaccuracies, which might lead to converging to a wrong solution 
-- this is explained in more detail in the documentation of `variational-lse-solver`.

## Citation

If you use the `variational-lse-solve` library or results from the paper, please cite our work as

```
Anonymious Citation
```

## Version History

Initial release (v0.1): March 2024

## License

Apache 2.0 License
  