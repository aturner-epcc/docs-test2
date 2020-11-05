# LAMMPS

<div class="warning">

<div class="admonition-title">

Warning

</div>

The ARCHER2 Service is not yet available. This documentation is in
development.

</div>

[LAMMPS](http://lammps.sandia.gov/), is a classical molecular dynamics
code, ("Large-scale Atomic/Molecular Massively Parallel Simulator").
LAMMPS has potentials for solid-state materials (metals, semiconductors)
and soft matter (biomolecules, polymers) and coarse-grained or
mesoscopic systems. It can be used to model atoms or, more generically,
as a parallel particle simulator at the atomic, mesoscopic, or continuum
scale.

## Useful Links

  - LAMMPS Documentation <https://lammps.sandia.gov/doc/Manual.html>
  - LAMMPS Mailing list details <https://lammps.sandia.gov/mail.html>

## Using LAMMPS on ARCHER2

LAMMPS is freely available to all ARCHER2 users.

The centrally installed version of LAMMPS is compiled with all the
standard packages included: <span class="title-ref">ASPHERE</span>,
<span class="title-ref">BODY</span>,
<span class="title-ref">CLASS2</span>,
<span class="title-ref">COLLOID</span>,
<span class="title-ref">COMPRESS</span>,
<span class="title-ref">CORESHELL</span>,
<span class="title-ref">DIPOLE</span>,
<span class="title-ref">GRANULAR</span>,
<span class="title-ref">KSPACE</span>,
<span class="title-ref">MANYBODY</span>,
<span class="title-ref">MC</span>, <span class="title-ref">MISC</span>,
<span class="title-ref">MOLECULE</span>,
<span class="title-ref">OPT</span>, <span class="title-ref">PERI</span>,
<span class="title-ref">QEQ</span>,
<span class="title-ref">REPLICA</span>,
<span class="title-ref">RIGID</span>,
<span class="title-ref">SHOCK</span>,
<span class="title-ref">SNAP</span>, <span class="title-ref">SRD</span>.

We do not install any <span class="title-ref">USER</span> packages. If
you are interested in a <span class="title-ref">USER</span> package, we
would encourage you to try to compile your own version and we can help
out if necessary (see below).

## Running parallel LAMMPS jobs

LAMMPS can exploit multiple nodes on ARCHER2 and will generally be run
in exclusive mode using more than one node.

For example, the following script will run a LAMMPS MD job using 4 nodes
(128x4 cores) with MPI only.

    #!/bin/bash
    
    #SBATCH --job-name=lammps_test
    #SBATCH --nodes=4
    #SBATCH --ntasks=512
    #SBATCH --tasks-per-node=128
    #SBATCH --cpus-per-task=1
    #SBATCH --time=00:20:00
    
    # Replace [budget code] below with your project code (e.g. t01)
    #SBATCH --account=[budget code] 
    #SBATCH --partition=standard
    #SBATCH --qos=standard
    
    # Setup the job environment (this module needs to be loaded before any other modules)
    module load epcc-job-env
    
    module load lammps
    
    srun --cpu-bind=cores lmp -i in.test -o out.test

## Compiling LAMMPS

The large range of optional packages available for LAMMPS, and
opportunity for extensibility, may mean that it is convenient for users
to compile their own copy. In practice, LAMMPS is relatively easy to
compile, so we encourage users to have a go.

Compilation instructions for LAMMPS on ARCHER2 can be found on GitHub:

<https://github.com/hpc-uk/build-instructions/tree/master/LAMMPS>

If you get stuck, please contact the Service Desk.
