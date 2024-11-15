Docker Template for Unraid: asustor-hardware

This docker template uses the https://github.com/mafredri/lcm/ repository. 

The openlcmd application interacts with LCM devices via a serial interface.

Features
Runs the openlcmd application to communicate with LCM devices.
Provides access to serial devices (/dev/ttyS1) from within the container.
Pre-configured Docker template for easy deployment on Unraid.

Installation
Prerequisites
Unraid server with Docker enabled.
A serial device available at /dev/ttyS1.
Git installed on your local machine (optional for manual cloning).
Clone the Repository
bash
Copy code
git clone https://github.com/your_username/docker-unraid-openlcmd.git
cd docker-unraid-openlcmd
Build and Push Docker Image (Optional)
If you need to build the image manually:

bash
Copy code
docker build -t your_dockerhub_username/openlcmd:latest .
docker push your_dockerhub_username/openlcmd:latest
Deploy on Unraid
1. Copy Template to Unraid
Upload the XML template file to your Unraid server:

bash
Copy code
scp unraid_template/openlcmd.xml root@<your-unraid-ip>:/boot/config/plugins/dockerMan/templates-user/
2. Add Docker Container
Log in to your Unraid server UI.
Navigate to Docker > Add Container.
Select the openlcmd template from the list.
Configure any additional settings as needed (e.g., container name, paths).
3. Ensure Serial Port Access
In the container settings, map /dev/ttyS1 from the host to the container as /dev/ttyS1.
Set the container to run in privileged mode.
Usage
Starting the Container
Start the container from the Unraid Docker interface.
The openlcmd application will automatically run and interact with the LCM device.
Logs
View logs to ensure everything is working correctly:

bash
Copy code
docker logs <container-name>
File Overview
Dockerfile: Defines the steps to build the container.
unraid_template/openlcmd.xml: Pre-configured Unraid template for the container.
README.md: This file, providing installation and usage instructions.
Contributing
If you'd like to contribute to this project, feel free to fork the repository and submit a pull request. Feedback and suggestions are welcome!


