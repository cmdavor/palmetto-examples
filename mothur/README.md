## mothur

This page instructs how to install mothur software to Palmetto The code and the
issue tracker can be found
[here](https://github.com/mothur/mothur/blob/master/INSTALL.md)

1. Request an interactive session. For example:

   ```
   $ salloc --nodes=1 --ntasks=1 --cpus-per-task=6 --mem=24G --time=3:00:00 # Changed from using qsub command to salloc instead for uniformity with Slurm.
   ```

2. Make a mothur directory in software_slurm. # Added this part for uniformity

   ```
   $ cd ~
   $ mkdir -p software_slurm/mothur
   $ cd software_slurm/mothur

   ```

3. Load the required modules # Removed openmpi

   ```
   $ module load gcc/12.3.0 # Updated from 8.2.0 to 12.3.0
   $ module load hdf5/1.14.3 # Updated from 1.10.1 to 1.14.3
   $ module load boost/1.84.0 # Updated from 1.65.1 to 1.84.0
   ```

4. Download mothur from
   [source](https://github.com/mothur/mothur/releases/tag/v1.48.0). Here we
   download the latest version 1.48.0 # Updated out of date version of mothur from 1.41.3 to 1.48.0

   ```
   $ wget https://github.com/mothur/mothur/archive/refs/tags/v1.48.0.tar.gz
   ```

5. Unpack the downloaded file and go into mothur source folder

   ```
   $ tar -xvf v1.48.0.tar.gz
   $ cd mothur-1.48.0
   ```

6. Modify the Makefile. # Updated the Makefile so it uses latest software versions

   ```
   $ nano Makefile
   #Replace the following lines 22-32 with information: (Note: username should be replaced)
    OPTIMIZE ?= yes
    USEREADLINE ?= yes
    USEBOOST ?= yes
    USEHDF5 ?= no
    LOGFILE_NAME ?= no
    BOOST_LIBRARY_DIR ?= "/software/boost/1.84.0/lib"
    BOOST_INCLUDE_DIR ?= "/software/boost/1.84.0/include"
    MOTHUR_FILES ?= \"\/home\/username\/applications\/bin\/mothur\"
    MOTHUR_TOOLS ?= \"\/home\/username\/applications\/bin\"
    VERSION = "1.48.0"
   ```

7. Run make file # Added make clean

   ```
   $ make clean
   $ make
   ```

8. The _mothur_ executable file will be created in the installation folder:
   **/home/username/applications/bin**. Make sure you set the correct
   environment PATH in ~/.bashrc file

   ```
   export PATH=$PATH:$HOME/applications/bin
   ```
