# tx2CudaDocker


## Background
This is a set of docker files to run some CUDA samples on the Nvidia Jetson tx2 installed with JetPack 3.2 - still in the preview phase at this date.

These files build on the work [here](). With JetPack 3.2 you don't have to actually build a new kernel, you just have to follow the instructions there for building the docker image for "devicQUery". 

However one that is working, one would like usually to see if the sample CUDA programs, espoecially those with nice OpenGL demos.

I got them to work by googling about and making small modifications to dockerfile used to build the docker image, and the tx2-docker bash script used to run them.

# Modificatins
Only two modifications were done to the tx2-docker script:
 - An addition volume mapping was added to the script (which was already set up to accomidate multiple mappings - and not all samples actually need that library)
 - An addition switch (--net=host) was added to the docker run command
 
The dockerfiles are more or less the same as the one for deviceQuery, except for the oceanFFT script which needs to load data, so an extra data directory was defined for that.

This has my Jetson TX2 compiled executables checked in to this directory, probably you want to use the ones you compiled on yours.

I goth the samples particles, oceanFFT, nbody, Mandlebrot and randomFog to work.

# Instructions

1. Clone this directory onto your machines.

2. Copy your locally compiled executables over mine.

3. Run the bash script "makedockers" to make all the docker images.

4. Run the bash script "rundockers" to run them all.

# Other samples

Generalizing to other samples should be straight forward. 

- If then need more data, follow the pattern in oceanFFT docker to make the data available for reading.
- If they need other libraries, look at the executable with the "ldd" command and make the appropriate changes to the NV_LIB bash script variable in "tx2_docker" and the LD_LIBRARY_PATH environment variable in the dockerfile.
