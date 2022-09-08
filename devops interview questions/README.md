# Devops Interview Questions And Answers

### 1. Why do we need git and why is it different from SVN?
* GIT is a commonly used version control system
* git tracks changes from you make and it you can revert to any version you want
* git also allows easy collaboration

## We have 2 types of VCS	
1. Centerilize VCS (subersion) - everybody push to the center repository. no working copy. branching is done on the central repo
2. distributed (3 layer aritechture) - you will have a local copy. branching can be done on local repo

### 2. Difference between git pull and git fetch?
git pull fetches the remote repository and also merge to the local branch but git fetch does half of the work. it fetches the remote repo and you merge the repo manually to the local branch by using 
```
git merge origin/remot-repo-name
```

### 3. How to clone a particular branch from remote repo?
```
git clone -b branch_name --single-branch remote_repo
```

### 4. What happens in the background when we do mvn install?
mvn clean delete the target folder

mvn install execute the following
* validate
* compile
* test
* package
* verify
* install
* deploy

5. settings you need to do before mvn deploy?
you need to have settings.xml where you specify your username and password of your server
you need to have you id in your porn.xml the matches the host in the settings.xml
also you need to specify the url/ip address where you artifact will go
copy your settings.xml to the ~/.m2/ folder
mvn install

6. why maven execution takes time in the first and second but less time in the third execuion
It downloads any dependency to the local repository on the first execution but uses the local repo to execute on the second and third time

7. how to get the present working directory?
basname "$PWD" or
pwd | rev | cut -d '/' -f 1 | rev

8. how to copy file from local machine to cloud linux machine
pscp file_name.ext username@ip:location

9 why we need ad-hoc commands and give scenario where you have used adhoc commands
Ansible ad-hoc commands uses the /usr/bin/ansible command-line tool to automate a single task on one or more managed nodes. Ad-hoc commands are quick and easy, but they are not reusable.

example
ansible --version
ansible all -i '324.323.42.32' -m ping 
ansible dev -i hosts -m ping
ansible dev -i hosts -m setup
ansible dev -i host -m copy -a 'src/home/sam/host dest=/home/sam/'

10. what is ansible.cfg file?
it is ansible configuration file where you can define settings for ansible. it is located at /etc/ansible

11. What are the modules you have worked on? which module will you use to get the a file from node to master
copy fetch, yum debug, get_url, expect, template, file, apt, command, shell
fetch module get the file from node to master

12. let say I have a plyabook which has 5 tasks in playbook, first 2 tasks should run on my local machine while the other task should run on node

13. How to save only last 5 build of a jenkins job?
Note: jenkins save all jobs in .jenkins/jobs folder
Go to configure select the max. number of builds - 5 and save

14 Have you worked on jenkinsfile? yes

15. Can we use docker in jenkinsfile as a node? Yes

16 who will handle docker container creation and deletion? This is handled by jenkins

17. If I am building a maven project always and docker container is fresh instance, it will try to download dependency from repository, what measures you will take to reduce
build time?
a. Download all the dependency your project needs on your hosts
b. copy the local repository into the container
c. add args '-v /root/.m2:/root/.m2/

18. What is multiple branch pipeline?
The multiplebranch pipleine project type enables you to implement different jenkinsfiles for different branches of the same project. Jenkins manages and executes the pipelines for each branch

19. If you forget jenkins password, how would you login back?
a. Go to jenkins folder cd ~/.jenkins
b. vi config.xml
c. check the usesecurity to false
d. logout
e. ps -eaf
f. kill jenkins PID kill -9 PID

20. Best Practices of Docker
a. Always keep Dokerfile in empty directory or make sure directory where Dockerfile present with required files
b. Use official images
c. Use more specific tags
d. Use multi stage build to remove build deps

21 Difference between docker stop and docker kill?
To see the live events on your hosts
docker events
docker stop gives sometime before killing the container but docker kill kills the container immediately.

22. Commands to list containers which state is exited?
docker ps -a -f status=running or exited or created
To remove the exited containers
docker rm $(docker ps -a -f status=exited -q)

23. Command to clean-up docker host(deleting stopped containers, dangling images and unused networks)?
docker system prune

23 Can we have multiple CMD in Dockerfile? Yes but only the last command will be taken into account

24 Have you worked on Docker swarm and Docker compose?
Yea docker swarm is a container orchestration tool, meaning that it allows the user to manage multiple containers deployed across multiple host machines.
Docker compose is a tool used to define and run multi-container applications

25 Can we have a multiple container in a pod?
Yes we can have a multiple container in a pod

26. Can we have similar containers in a pod?
No because pod is unique individual unit

27. How will you check if something fails in a pod
kubectl get all
kubectl describe pod pod_name

28. What is liveness and readiness probe?
this make your application highly available.

29. Have you worked on kubernetes monitoring?
kubernetes is a dynamic tool which creates and deletes pods and we need to know when this happens
and because of this we need to monitor the events

30. Can we deploy a pod on a particular node
 you can use node selector
kubectl apply -f file_name.yml 
kubectl get all
kubectl get all -o wide


31 How do you clone a last commit?
git clone -b branch_name --single-brach --depth 1 repo_link
git log --oneline

31. What is submodule and why do we need to use submodule?
A git submodule is a record within a host git repository that points to a specific commit in another external repository. Submodules are very static and only tracks
specific commits
Submodules do not track git refs or branches and are not automatically updated when the host repository is updated

31. How do you delete your files from staging area to your working directory?
git rm --cached filename 

32. What is multi module project
A multi-module project is built from an aggregator POM that manages a groupd of submodules.
In most cases the aggregator is located in the project's root directory and must have packaging of type pom
The submodules are regular maven projects, and they can be built separately or through the aggregator POM
note: if you have a multi-module project the packaging is pom
Two things needed in the parent pom
packaging - pom
modules - the sub projects

in the sub project you need to define the parent(groupId, artifactId, version)

33. configuration you need to do in parent and child project

34. What is dependency management
This is a core feature in maven
managing dependencies of multi-module projects and applications that consist of hundreds of modules is possible
maven helps a great deal in defining, creating and maintaining reproducible builds with well-defined classpaths and library versions
instead of defining dependencies individually in all the sub project you can define it ones on the parent pom and it will take effect on all the sub projects

35. What is Transitive Dependency?
This means that if A depends on B and B depends on C, then A depends on both B and C.
To view transitive dependency
mvn install:tree
To prevent transitive dependency
you can use exclusions

36. What is commit based job in jenkins?
Commit based job is when someone pushes to github it should trigger a job in jenkins
To achieve that you use webhooks in github

37. You want to create 50 freestyle jobs, witht the same configuration but only change is job name? how would you do this?

38. How do you copy a job in your local jenkins instance to other local jenkins instance?
1. cd /home/<username>
2. cd ~/.jenkins/
3. cd jobs
4. mkdir foldername
5. cd web-hooks
6. cp -r . ../foldername/

38. how to check if a port is used or not?
netstat -tupln

39. Command to get the number of lines in a file?
cat palin.sh | wc -l

40. Let say I have 4 machines consider 1 as ansible master other 3 as nodes, what are the basic setup you need to do to create ansible cluster?
prerequisite
you must have python installed on your system
1. sudo apt update
2. sudo apt install softwre-properties-common
3. sudo apt-add-repository ppa:ansible/ansible
4. sudo apt update
5. sudo apt install ansible

To verify your installation
ansible --version

you install ansible only your master

6. create ssh key in the master and copy public key to the nodes
ssh-keygen
ssh-copy-id root@ip_address
ssh root@ip_address

7. change some ssh settings
change root password: passwd root
/etc/ssh/sshd_config
change PasswordAuthentication Yes, permitRootLogin yes
systemctl restart sshd, service sshd restart

41. What are ansible roles?
Roles provides a framework for fully independent, or interdependent collections of variables, tasks, files, template and modules
Roles breaks down a playbook into multiple files. This simplifies writing complex playbooks and it makes them easier to reuse

42. What is Ansible galaxy?
Ansible galaxy create a role folder structure

43. What is ansible Facts?
Ansible collects pretty much all the information about the remote hosts as it runs a playbook. The task of collecting this remote system information is called gathering facts.
example ansible all -i "ip_address" -m setup

44. Can we have a windows machine as ansible master? No. As a node? Yes

45. Why do we need a multistage docker file?
It is on of the best practices and is used to reduce the file size of the image drastically. 

### 46. can you copy a file from local to a running container? Yes
```
docker cp file_name.ext container_id
```





