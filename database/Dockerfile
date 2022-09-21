FROM mysql:5.7

# set image environment variables
# don't put passwords here in real projects!
# use server environment variables instead.
ENV MYSQL_USER mysql_user
ENV MYSQL_PASSWORD mysql_password
ENV MYSQL_ROOT_PASSWORD mysql_root_password
ENV MYSQL_DATABASE visitlog

# copy the pre-written script to the folder where the script is executed 
# when creating the container in the docker environment.
COPY ./scripts/ /docker-entrypoint-initdb.d/

# command to build the image (in the same directory as this file)
# docker build -t {image_name} .

# execute command (to see the log in the terminal)
# docker run --name {container_name} -it -p 3306:3306 {image_name}

# execute command (run as demon)
# docker run --name {container_name} -p 3306:3306 -d {image_name}
