As February 2011,

# Knwown bugs - to be fixed in next release #

**If  you use the binary version for windows, and  cannot import pyffmpeg under windows, be sure to have also installed mingw/msys has it was compiled with msys and it is requiring a DLL related to gcc/g++.**

**It is actually better to remove avcodec in the list of linked libraries.**

# Limitations #

**Seeking is not performing well on network streams yet.** pyffmpeg is currently doing playback only, it does not support encoding
