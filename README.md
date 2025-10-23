# BlocksOS Image Generator 

## Pre-configurations 
Docker can only run with legacy ip_tables, new versions, such as Debian:trixie 
run with ip_tables (nf_tables) which is not compatible. 

To solve this issue, the docker image is build based on Debian:bookworm 
We can then create the Raspberry Pi image based on the latest Debian:trixie



## Image Generations



### Configuring the Image

### Running the build command

### Retrieving the Generated Image
After building the image we need to extract the generated image from inside the docker container. In order to do this follow the instructions bellow:

    On wsl or host machine 

    1. Get the id of the image generator container 
        
    2. Then run the command: 

        sudo docker cp <container id>:/home/<container user>/rpi-image-gen/work/<Image Name>/deploy/<Image Name>.img ~/<Host directory>




### Run container 

sudo docker compose up -d 

sudo docker exec -it rpi-imagegen /bin/bash




Can make changes on the config/post-build.sh script so things are setup after 

Need to add executable to the file if it's not set




./build.sh -o ~/blocks/blocks.options -D ~/blocks -c blocks