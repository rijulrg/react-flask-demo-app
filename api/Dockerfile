# We Use an official Python runtime as a parent image
FROM python:3.7
# The enviroment variable ensures that the python output is set straight
# to the terminal with out buffering it first
ENV PYTHONUNBUFFERED 1

# Update and upgrae Package Libraries
RUN apt-get update && apt-get upgrade -y && apt-get autoremove && apt-get autoclean

# Set the working directory 
WORKDIR /usr/smartcow/app

# Copy the current directory contents into the container 
COPY  requirements.txt /usr/smartcow/app

# Install any needed packages specified in requirements.txt
RUN pip install -r requirements.txt

# Copy required files
ADD . /usr/smartcow/app

# Command to start gunicorn using script
RUN chmod +x ./entrypoint.sh
ENTRYPOINT ["sh", "entrypoint.sh"]
