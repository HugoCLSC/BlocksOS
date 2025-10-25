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

Emulation work around on binfmt_misc [binfmt workaround](https://github.com/tonistiigi/binfmt)


sudo docker compose up -d 

sudo docker exec -it rpi-imagegen /bin/bash




Can make changes on the config/post-build.sh script so things are setup after 

Need to add executable to the file if it's not set




./build.sh -o ~/blocks/blocks.options -D ~/blocks -c blocks





### Layers


- Layers are module, composable components that define specific aspects of your Raspberry Pi build 
- Each layer encapsulates a specific and focussed piece of functionality and can declare dependencies on other layers, creating a flexible build system. 


1. Device layers -> Hardware specific 
2. Image Layers -> image specific configurations, disk layout etc 
3. General Layers -> Reusable configuration snippets, utilities, groups of related functionality
4. Suites -> A layer providing a particular baseline of device functionality



How are layers used 

Layer structure 

each layer is YAML file containing: 
    1. X-Env Metadata: mandatory. Layer attributes, variable declaration, dependencies 
    2. mmdebstrap configuration: Optional. Package lists, repository mirrors, scripts 


Build process 

    

    ./rpi-image-gen build -S /home/imagegen/BlocksOS/blocks -c /home/imagegen/BlocksOS/blocks/config/blocks-config.yaml  -B /home/imagegen/BlocksOS/



    This will output the image file on BlocksOS/image-blocksos/BlocksOS.img



./rpi-image-gen build -I -S /home/imagegen/BlocksOS/blocks -c /home/imagegen/BlocksOS/blocks/config/blocks-config.yaml  -B /home/imagegen/BlocksOS/build 2>&1 | tee /home/imagegen/BlocksOS/output.txt 



sudo docker cp blocks d3c28ab9d345a9fc7b66a2444f11fe6dca8dcca40b28ffd009571f86cad2e265:/home/imagegen/BlocksOS/


sudo chown -R imagegen ~/BlocksOS
sudo chown -R imagegen ~/rpi-image-gen


sudo docker cp d3c28ab9d345a9fc7b66a2444f11fe6dca8dcca40b28ffd009571f86cad2e265:/home/imagegen/BlocksOS/image-blocksos/ /mnt/c/Users/hugos/Documents/BlocksOS.img
