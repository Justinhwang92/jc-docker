FROM node:12.18.4

# command to run when creating the image
RUN npm install -g http-server 

# set directory for the commands to run in
WORKDIR /home/node/app

# commnd to run when starting the container
CMD ["http-server", "-p", "8080", "./public"]

# command to create image (in the same directory as this file)
# docker build -t {image_name} .

# create container & executor
# docker run --name {container_image} -v $(pwd):/home/node/app -p 8080:8080 {image_name}