GEM5 Statistics
=====

This repository contains a script to convert [GEM5][gem5] simulation statistics to [McPAT][mcpat] compatible inputs.

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
This repository contains a sample GEM5 generated stats file, a processor
configuration file produced by GEM5 and a McPAT template file. To run
GEM5ToMcPAT.py use:  
`GEM5ToMcPAT.py stats.txt config.json template-xeon.xml`

The above command will produce mcpat-out.xml file. mcpat-out.xml can be used in the usual
way with McPAT.  
`<mcpat-bin> -infile mcpat-out.xml`

Internals
----------
h3. Preparing Template File
The above example uses a template file created by modifying
ProcessorDescriptionFiles/Xeon.xml from McPAT. The parameters in Xeon.xml that
should be replaced with a value from GEM5 configuration (config.json) should be
replaced with config.<parameter\_path>. For example,  
<`param name="number_hardware_threads" value="2"/>`  
should be replaced by  
`<param name="number_hardware_threads" value="config.system.cpu.numThreads"/>`  
Any standard computation in python-supported format is allowed. For example, the
following is acceptable:  
`<param name="target_core_clockrate" value="1e-6/config.system.cpu_clk_domain.clock"/><!--MHz -->`  

Similarly, statistic that should be replaced with values from GEM5 statistics
(stats.txt) should be replacd with stats.<stat\_path>. For example,  
`<stat name="total_cycles" value="100000"/>`  
should be replaced by
`<stat name="total_cycles" value="stats.system.cpu.numCycles"/>`  
in the template file.

h3. Modifying Script 
dumpMcpatOut function in the script is the workhorse. It first replaces all the
config parameters by using the values from config.json and subsequently works on
stats parameters.


Miscellaneous
--------
These scripts are inspired by [m5-mcpat.pl][sicsa] script but implemented in python instead of perl.

[sicsa]: https://www.cl.cam.ac.uk/~acr31/sicsa/
