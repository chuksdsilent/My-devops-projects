Docker

In Docker we isolate our services like ngnix, tomcat, apache etc

To isolate our services we need VM's/Cloud Computing to setup infra

We isolate our service in OS

Because of isolation we end up setting up multiple VM's/Instances

VM's/Instances will be overprovisioned

Results in high CapEx and OpEx

Every VM needs

OS and OS needs maintenance
OS also needs Licensing
OS also Takes time to boot

VM's are portable(i.e it can be moved to server or to local) but they are bulky
VM's also need s alot of resources

Point to note

isolating services are important

high availablity achived by multiple instances/vm's

portability matters or eases the deployment

Container
Container share the machines' OS system kernel and therefore do not require OS per application

A container is a standard unit of software that packages up 
  code
  dependencies
but does not use different operating systems

comparing VM vs Containers

container uses one operating system while vms uses different operating systems
container boot up faster than vms
container are processes
container offer isolation while vms offer virtualization
containers are OS virtualization
VM are are hardware virualization

Docker is container virual environment. Docker manages container


