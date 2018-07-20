SSH keys 
-	Id_rsa – “the key”  (private key)
-	Id_rsa.pub – given to external sytem  “the lock” (public key)
-	Public key file saved on laptop as ‘public key’

Amazon EC 2
-	Log into AWS -> services -> ec2 (within compute)
-	Setup SSH keys on ec2: import key pair, give it a name, and paste public key 
-	Launch a new instance 

Security Groups
-	create new security group (name unimportant) 
-	Potential Groups: 
-	type = SSH, port = 22
-	type = http, port = 80
-	type = https, port = 443
-	PostgreSQL, port = 5432
-	Custom TCP rule = 27016 (for mongo – note that typical port is 27017)
-	All source fields set to ‘anywhere’
-	create security group 

AWS Operating System
-	we use Ubuntu in the course – choose the ubuntu operating system that comes free 
-	to connect to the ubuntu system: use bash and type “ ssh: ‘public ip’ “

Docker Installation: In bash - 
-	curl - sSL https://get.docker.com | sh
-	sudo usermod – aG docker Ubuntu 
-	ctrl-d twice

Obtaining the correct Docker image
-	tmux
-	docker pull ‘jupyter/datascience-notebook
Running the correct Docker image as a container
-	docker pull hello-world 
-	docker run hello-world 
       **Tests docker connection**
-	once the download is complete: “docker run  -d -p 443:8888  -v /home/Ubuntu:/home/jovyan jupyter/datascience- notebook” (now denoted by j)
-	docker logs ‘first 3 #s of container id’ (retrieves token)
-	-use token in bash line into pw line (yes, the whole thing)

once the download is complete: 
-	“docker run  -d -p 443:8888  -v /home/Ubuntu:/home/jovyan jupyter/datascience- notebook” (now denoted by j)
-	docker logs ‘first 3 #s of container id’ (retrieves token)
-	-use token in bash line into pw line (yes, the whole thing

Jupyter notebook security concerns
-	to access notebook, input public IP address (found in EC2 launch summary) and add ‘:443’ 
-	important to use https port to connect because of the public state of the connection 
-	once connected to the server homepage, enter the hashed password (from ‘docker run...’ sequence in bash) to enter notebook securely 

Create at least one diagram of your overall system.
Security Groups Diagram: 



A detailed budget of the costs of running a Jupyter Data Science Notebook Server for three months using at least three different kinds of EC 2 instances.
Option 1: 
Usage: General Purpose On Demand
Host Server: m5.4xlarge
Location: US West (Oregon)
Hourly Rate: $ 0.77
Monthly: $ 516.10
3 Month Total Cost: $1,548.29

Option 2: 
Usage: Reserve Instance
Host Server: t2.small
Location: US West (Oregon)
Hourly Rate: $ 0.08
Monthly: $ 54.31
3 Month Total Cost: $162.93

Option 3: 
Usage: Dedicated Host
Host Server: m4
Location: US West (Oregon)
Hourly Rate: $ 1.63
Monthly: $ 1094.27
3 Month Total Cost: $3,282.81
