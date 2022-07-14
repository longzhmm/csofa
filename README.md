# csofa is the C++ version of the SOFA software
SOFA (Standards Of Fundamental Astronomy) software package is a subroutine library of astronomical basic standards written by IAU. At present, there are a total of 161 subroutines, which are mainly written in Fortran F77 and ANSI C. Each subroutine is placed in a .f file. Its main content includes two aspects: basic vector operations and astronomical basic standards.

Since Fortran 77 does not support basic operations on matrices and vectors, such as matrix multiplication, etc. So SOFA has some subroutines for this. On this basis, the subroutines of the astronomical basic standard are written, including: Julian day calculation of UTC time; based on the 1976 precession and 1980 nutation standards from the earth-fixed coordinate system (ITRF) to the J2000 geocentric celestial coordinate system (GCRF) Transformation matrices (which also contain the latest IAU 2000 and 2006 standards); and calculations of solar system planetary ephemeris, etc.

All these subroutines are compiled according to the relevant standards of the IAU, there are detailed notes in the program, and there are relevant instructions in the documentation, which is very easy to read.

SOFA description and download address: https://iausofa.org/

All these subprograms are compiled according to the relevant standards of the IAU. There are detailed comments in the program, and there are also relevant instructions in the documentation under the doc folder. It is very easy to read.

"manual.pdf" contains the function descriptions and interface descriptions of all subroutines in the SOFA software package; "sofa_pn.pdf" contains the descriptions of the IAU 2000 and IAU 2006 precession nutation models, as well as the detailed conversion process from ITRS to GCRS.
