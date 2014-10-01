GEM5 Statistics
=====

This repository contains a script to convert [GEM5][gem5] program run statistics to [McPAT][mcpat] compatible inputs.

[gem5]: http://www.gem5.org/Main_Page
[mcpat]: http://www.hpl.hp.com/research/mcpat


Quick Start
----------

Use the following command to invoke the script:
`GEM5ToMcPAT.py [options] <gem5 stats file> <gem5 config file (json)> <mcpat template file>`

For options, Please see:
`GEM5ToMcPAT.py -h`


What Else
--------
This script is inspired by [m5-mcpat.pl][sicsa] script but implemented in python instead of perl.

[sicsa]: https://www.cl.cam.ac.uk/~acr31/sicsa/
