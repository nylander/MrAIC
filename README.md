MrAIC
=====

README file for MrAIC.pl 1.4.6 -- 2014-June-02

MrAIC.pl 1.4.6 by Johan A. A. Nylander

E-mail: jnylander @ users.sourceforge.net

See also: https://github.com/nylander/pMrAIC

Description
-----------

MrAIC.pl is a Perl script for calculating AIC, AICc, BIC, and Akaike weights 
(for a review, see Burnham and Anderson, 2002) for nucleotide substitution 
models. Likelihood scores under different models are estimated using PHYML 
(Guindon and Gascuel, 2003).

Input is DNA data in PHYML format (see below).

If the argument -modeltest is parsed, 56 models (the ones tested in Modeltest 
[Posada and Crandall, 1998]) are evaluated in PHYML. Default is to test the 24 
models that can be specified in MrBayes v3 (Ronquist and Huelsenbeck, 2003). 
These are JC, F81, K2P (aka K80), HKY, SYM and GTR, each combined with Propinv 
(I) and/or Gamma (G).

A difference between Modeltest and MrAIC.pl is that MrAIC.pl does not evaluate 
all models on the same, approximate topology. Instead, PHYML is used to try to 
find the maximum of the likelihood function under all models. This is necessary 
for finding AIC, AICc, or BIC for the models.

Requirements
------------

1) Perl (see also ActivePerl) must be installed on your system.

2) PHYML (Guindon and Gascuel, 2003) version 3 must be installed on your system 
(named "phyml" and be in the PATH). Alternatively, user might edit MrAIC.pl to 
specify the full path to the PHYML binary.

Windows users: Make sure you have set the environment variables to include an 
executable named "phyml.exe". Alternatively, rename/copy/link the phyml_w32.exe 
to phyml.exe and put it in the same folder as the mraic.pl script.


Usage
-----

Interactively or by passing arguments as below

    mraic.pl infile
    mraic.pl -modeltest infile

where infile contain DNA data in PHYML format which is somewhat similar to the 
PHYLIP format (see example files dat.txt and dati.txt).
Example, "sequential" format (note the space between taxon name and sequence):

    3 8
    Taxon_1 ACGTACGT
    Taxon_2 ACGTACGT
    Taxon_3 ACGTACGT


Notes
-----

In this script, sample size (n) used in AICc and BIC is assumed to be the 
number of characters in the data matrix. This is probably not correct when it 
comes to phylogenetic analyses (Nylander, 2004), but serve as an approximation 
to the true n.
Branch lengths are included when specifying the total number of parameters for 
the models.
AICc values are only printed if the number of parameters are high compared to 
number of characters (Nchar/Max.Number of parameters < 40). Maximum number of 
free parameters is 10 (for the GTR+I+G model) plus the number of branch 
lengths. The limit of 40 is a heuristic suggested by Burnham & Anderson (2002).
Furthermore, all calculations of Akaike weights, AIC, AICc, and BIC are all 
dependent on PHYML's ability to find the maximum of the likelihood under each 
model. More elaborate searches might be necessary to get more correct 
assessment of the ML for some data sets!


Acknowledgements
----------------

Thanks to Torsten Eriksson for advice on slick Perl programming.


Suggested reference for MrAIC.pl
--------------------------------

Nylander, J. A. A. 2004. MrAIC.pl. Program distributed by the author. 
Evolutionary Biology Centre, Uppsala University.


Other References
----------------

Burnham, K. P., and D. R. Anderson. 2002. Model selection and multimodel 
inference, a practical information-theoretic approach. Second edition. 
Springer, New York.

Guindon, S., and O. Gascuel. 2003. A simple, fast, and accurate algorithm to 
estimate phyogenies by maximum likelihood. Systematic Biology, 52:696-704:

Nylander, J. A. A. 2004. Bayesian phylogenetics and the evolution of Gall 
wasps. Comprehensive Summaries of Uppsala Dissertations fro the Faculty of 
Science and Technology 937. Uppsala University.

Posada, D., and K. A. Crandall. 1998. MODELTEST: Testing the model of DNA 
substitution. Bioinformatics 14:817-818.

Ronquist, F., and J. P. Huelsenbeck. 2003. MRBAYES 3: Bayesian phylogenetic 
inference under mixed models. Bioinformatics 19:1572-1574.


License and Copyright
---------------------

Copyright (c) 2004-2014 Johan Nylander

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
