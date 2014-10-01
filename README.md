GPGPU-sim
=========

This repo was forked from git://dev.ece.ubc.ca/gpgpu-sim

**upstream** branch tracks points to latest known state of git://dev.ece.ubc.ca/gpgpu-sim
**master** branch contains general fixes and improvement on top of upstream
**custom** branch adds specific features such as adding custom instructions

## Adding a custom ptx instruction:

Everything happens in `v3.x/src/cuda-sim`.
* Add your custom definition in `opcodes.def`
* Add your instruction in the ptx lexer file `ptx.l`
* Find a suitable substitute to use in ptxas and define it in `substitutes.h`
* If you specified a custom implementation, add it in `instructions.cc`

**note :** A piece of code containing invalid ptx instruction will fail in ptxas, therefore you must make sure ptxas is not invoked while compiling your code. Be sure however to include the ptx assembly code in the final binary (during the fatbinary step) since this is what gpgpu-sim will use to run the simulation.