GEM5 Statistics
=====

This repository contains a script to convert [GEM5][gem5] program run statistics to [McPAT][mcpat] compatible inputs.

[gem5]: http://www.gem5.org/Main_Page
[mcpat]: http://www.hpl.hp.com/research/mcpat


Quick Start
----------

Use the following command to invoke the script:

`GEM5ToMcPAT.py [options] <gem5 stats file> <gem5 config file (json)> <mcpat template file>`


For more options, please run:

`GEM5ToMcPAT.py -h`

Example
----------
This repository also contains a sample GEM5 generated stats file, a processor
configuration file produced by GEM5 run and a McPAT template file. To run
GEM5ToMcPAT.py use:

`GEM5ToMcPAT.py stats.txt config.json template-xeon.xml`

It will produce mcpat-out.xml file. mcpat-out.xml can be used in the usual
way with McPAT.

`<mcpat-bin> -infile mcpat-out.xml`

Internals
----------

Miscellaneous
--------
These scripts are inspired by [m5-mcpat.pl][sicsa] script but implemented in python instead of perl.

[sicsa]: https://www.cl.cam.ac.uk/~acr31/sicsa/
