# tx2CudaDocker

This is a set of docker files to run some CUDA samples on the jetson tx2 installed with JetPack 3.2 - still in the preview phase at this date.

These files build on the work [here](). With JetPack 3.2 you don't have to actually build a new kernel, you just have to follow the instructions there for building the docker image for "devicQUery". 

However one that is working, one would like usually to see if the sample CUDA programs, espoecially those with nice OpenGL demos.

I got them to work by googling about and making small modifications to dockerfile used to build the docker image, and the tx2-docker bash script used to run them.

Only two modifications were done to the tx2-docker script:
 - An addition volume mapping was added to the script (which was already set up to accomidate multiple mappings - and not all samples actually need that library)
 - An addition switch (--net=host) was added to the docker run command
 
The dockerfiles are more or less the same as the one for deviceQuery, except for the oceanFFT script which needs to load data, so an extra data directory was defined for that.

