# axis-common-node-red: objectpath
Node-RED environment/configuration for objectpath-abalyzer.  The ObjectPath application needs to be cloned from the Node-RED projects.

# pre-requisites
- Linux host with Docker, Docker-compose and GIT installed

# Container configuration
You may want to alter the docker-compose default settings based on your environment
- Port = 8640
- Timezone = Europe/Stockholm
- objectpath-nodered (if you paln to have multiple instance)

# Node-RED configuration
You may want to alter the default configuration of Node-RED based on your environment
- httpAdminRoot: '/admin',   (Default flows view url http://address:8600/admin)
- ui: { path: "/" },         (Default dashboard url http://address:8600/)
- adminAuth:                 (Default disabled.  It is recommended that you enable admin credentials.  See [Securing Node-RED](https://nodered.org/docs/user-guide/runtime/securing-node-red#editor--admin-api-security))
- httpNodeAuth:              (Default disabled.  It is recommeded to enable credentials to dashboard view. See [Securing Dasboard](https://nodered.org/docs/user-guide/runtime/securing-node-red#http-node-security))
- contextStorage:            (Default enabled.  Contect data will be stored and retained between reboots)
- projects:                  (Default enable.  Allows to revisioning of local projects or import remote repositories)  
- credentialSecret           (Set your own key to encrypt sensative data on host)

# Deployment
### Clone repository (e.g. from /home/user/ )
```
git clone https://github.com/pandosme/axis-common-node-red.git
cd axis-common-node-red
```
### Switch to OnbjectPath branch
```
git checkout objectpath
```
### Install node-red and mongo containers
```
sudo docker-compose pull
```
### Install npm packages. 
The following additional packages will be installed
- [Dashboard](https://flows.nodered.org/node/node-red-dashboard)
- [UI Table](https://flows.nodered.org/node/node-red-node-ui-table)
- [Axis device & Axis Camera](https://flows.nodered.org/node/node-red-contrib-axis-device)
- [MongoDB](https://flows.nodered.org/node/node-red-node-mongodb)

If nodejs and npm is installed on your system run,
```
sudo npm install
```
If nodejs and npm is not installed run
```
sudo docker-compose up -d
sudo docker exec -it axis-common-node-red bash
cd /data
npm install
exit
sudo docker-compose down
```
## Start container
```
sudo docker-compose up -d
```
Access Node-RED with a browser
```
Flows http://address:8640/admin
Dashboard http://address:8640
```
## Clone ObjectPath application
Follow instructions on [objectpath-analyzer](https://github.com/pandosme/objectpath-analyzer)
