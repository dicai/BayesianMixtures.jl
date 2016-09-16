This folder contains the files for Peter Green's Nmix program for univariate normal mixtures with a prior on the number of components. This implements the reversible jump MCMC (RJMCMC) approach of Richardson and Green (1997), Journal of the Royal Statistical Society: Series B, 59(4), 731-792.
https://people.maths.bris.ac.uk/~mapjg/Nmix/

----------------------------------------------------------------------
## Contents

- Nmix.zip - Source files for Windows.
- Nmix.tar.gz - Source files for Unix-like environments (including Mac OSX and Linux).

----------------------------------------------------------------------
For Peter Green's instructions, see the readme.txt file in Nmix.zip or Nmix.tar.gz. 

Below is the process I used to compile Nmix on Mac and Windows.

### Mac OS X

- Install gfortran by following the instructions here: https://gcc.gnu.org/wiki/GFortranBinariesMacOS
- Unpack Nmix.tar.gz and run the following commands in the resulting folder:
    gcc -c -o sd.o -DRETS -DSUNF sd.c
    gfortran -O2 -o Nmix Nmix.f pnorm.f algama.f rgamma.f gauss4.f sd.o
- Move the resulting binary ("Nmix") to the examples folder. Make sure Nmix is executable: chmod +x Nmix.

### Windows

- If the provided Nmix.exe executable works for you (examples/Nmix.exe), then you're good to go.  Otherwise, read on.
- Install gfortran by following the detailed instructions here: http://www.mingw.org/wiki/Getting_Started
    Choose to install mingw32-base, mingw32-gcc-fortran, and msys-base.
- Unzip Nmix.zip and copy the contents to your MSYS home directory, e.g., C:\MinGW\msys\1.0\home\jeff\.
- Start MSYS and run the following commands in the folder containing the Nmix source files:
    gcc -c -o sd.o -DRETS -DSUNF sd.c
    gfortran -O2 -static -o Nmix Nmix.f pnorm.f algama.f rgamma.f gauss4.f sd.o
- Move the resulting executable ("Nmix.exe") to the examples folder. 


