# Electronic structure of C<sub>60</sub>

Useful links:
- [Qbox code](http://qboxcode.org/)
- [Qbox commands](http://qboxcode.org/doc/html/usage/commands.html)
- [Qbox variables](http://qboxcode.org/doc/html/usage/variables.html)
- [SG15 Pseudopotentials](http://www.quantum-simulation.org/potentials/sg15_oncv/xml/)

Interaction with the scheduler:

- `sbatch name_of_script.sh`: submit a job to the scheduler, a job_id will be generated
- `squeue -u $USER`: query status of all my jobs, job_ids can be retrieved from the output of this command
- `scancel job_id`: cancel the job identified by job_id

Legend:
- <i>CFU: Check For Understanding</i>
- <i>Q: Question</i>

## 1. LDA ground state

Input: `qb1.in`

Submission: `sbatch submit1.sh`

Output: `qb1.out`

- Check total energy: `./extract_etotal.sh qb1.out`
  - <i>CFU: How many self-consistent steps did the code do?</i>
- Check single particle energies: `./extract_eigenset.sh qb1.out`
  - <i>CFU: Why do we have 120 single particle energies?</i>
- Check maximum force: `./qbox_maxforce.py qb1.out`

## 2. PBE ground state

Input: `qb2.in`

Submission: `sbatch submit2.sh`

Output: `qb2.out`

- Check total energy: `./extract_etotal.sh qb2.out`
- Check single particle energies: `./extract_eigenset.sh qb2.out`
- Check maximum force: `./qbox_maxforce.py qb2.out`

## 3. PBE0 ground state

Input: `qb3.in`

Submission: `sbatch submit3.sh`

Output: `qb3.out`

- Check total energy: `./extract_etotal.sh qb3.out`
- Check single particle energies: `./extract_eigenset.sh qb3.out`
- Check maximum force: `./qbox_maxforce.py qb3.out`
  - <i>Q: Which exchange-correlation functional gives largest forces?</i>

## 4. Geometry optimization at LDA

Input: `qb4.in`

Submission: `sbatch submit4.sh`

Output: `qb4.out`

- Check maximum force as a function of structural minimization: `./qbox_maxforce.py qb4.out`
  - <i>CFU: Are forces getting smaller?</i>
- Visualize with [VMD](https://www.ks.uiuc.edu/Research/vmd/): `./qbox_xyz.py -all qb4.out > trajectory.xyz`
