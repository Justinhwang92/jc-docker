FROM python:3.8.5

# command to run when creating the image
RUN pip3 install flask flask-cors flask-mysql

# set directory for the commands to run in
WORKDIR /usr/src/app

# commnd to run when starting the container
CMD ["python3", "backend.py"]

# command to create image (in the same directory as this file)
# docker build -t {image_name} .

# create container & executor
# docker run --name {container_image} -v $(pwd):/usr/src/app -p 5000:5000 {image_name}