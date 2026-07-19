DevOps Practice Project – Dist Directory

# Application-Deployment-1
GitHub (Source)
│
▼
CodePipeline
│
├── Source Stage  → Pulls code via GitHub App connection
│
├── Build Stage    → CodeBuild: docker build → push to Docker Hub
│
├── Test Stage     → CodeBuild: runs test/validation steps
│
└── Deploy Stage   → CodeBuild: kubectl apply → Amazon EKS
│
▼
EKS Cluster (brain-cluster)
│
┌───────────┴───────────┐
▼                       ▼
Deployment (2 pods)      Service (LoadBalancer)
brain-task-deployment    brain-task-service
│                       │
└───────────┬───────────┘
▼
Public URL (AWS ELB)
│
▼
End Users / Browser


<img width="1467" height="562" alt="image" src="https://github.com/user-attachments/assets/513992fa-cfad-4fc9-8455-8eeaec3a7600" />



Launch Ubuntu EC2
Ubuntu 24.04
t3.medium 
30 GB storage

<img width="1911" height="735" alt="image" src="https://github.com/user-attachments/assets/bdd1fbb9-cc93-4047-a226-0b8448cfffd3" />
<img width="1761" height="732" alt="image" src="https://github.com/user-attachments/assets/44dfc816-ab5e-4ae4-8a2d-a9614aa6b7da" />
<img width="1643" height="687" alt="image" src="https://github.com/user-attachments/assets/a2766fad-a3ac-4a22-ab1e-f031535a793d" />
<img width="1615" height="403" alt="image" src="https://github.com/user-attachments/assets/8853c4bf-4422-4c1b-867c-7338b405d725" />

Install Docker and allow ubuntu user 

<img width="1903" height="552" alt="image" src="https://github.com/user-attachments/assets/5c8f2774-1de7-47f3-9ef2-70962a98dd98" />

Clone Repository

<img width="1907" height="826" alt="image" src="https://github.com/user-attachments/assets/5eef0883-3df6-4543-b1a7-0f3163801f23" />

Install NodeJS and check verion and install npm node package manager

<img width="1917" height="153" alt="image" src="https://github.com/user-attachments/assets/5b8c2eb0-a95e-45b9-9312-a6644015484c" />

Repository already contains the built application the dist folder is the output of: npm run build
<img width="1907" height="533" alt="image" src="https://github.com/user-attachments/assets/e49b6270-cd16-42d9-92da-cea841f708f4" />

Create a Docker Hub Repository
<img width="1892" height="863" alt="image" src="https://github.com/user-attachments/assets/f0af82c7-d733-4dde-9b3a-30d4685ba849" />

Create docker file and build the image and confirm
<img width="1895" height="772" alt="image" src="https://github.com/user-attachments/assets/acaf3282-88b5-4c63-8b75-2fe41f28df30" />

Test the Image Locally and check using public ip  http://<EC2-PUBLIC-IP>:3000
<img width="1902" height="166" alt="image" src="https://github.com/user-attachments/assets/b4344229-fbe1-4cad-892b-2889e72d2bf0" />
<img width="1912" height="945" alt="image" src="https://github.com/user-attachments/assets/33443041-3d32-4756-9646-1c3f2740aad3" />

Login to Docker Hub and push the images to docker repo
<img width="1913" height="286" alt="image" src="https://github.com/user-attachments/assets/a2165a4a-eee1-46bf-8def-d927571fe938" />
<img width="1908" height="393" alt="image" src="https://github.com/user-attachments/assets/dd4e2f7d-c78c-448e-9356-53a601da9b19" />
<img width="1222" height="603" alt="image" src="https://github.com/user-attachments/assets/a92a38db-9dc7-4a74-9502-5be0c89de035" />

Configure AWS CLI 
<img width="1906" height="336" alt="image" src="https://github.com/user-attachments/assets/032a09d7-bfd1-4517-ba14-69f8c0b90d1a" />

Install and verify kubectl and eksctl
<img width="1917" height="322" alt="image" src="https://github.com/user-attachments/assets/f6108763-f477-48be-a6ef-97d494e4b499" />

Create Cluster
<img width="1862" height="538" alt="image" src="https://github.com/user-attachments/assets/fc1f6f3a-9f9a-4670-ab78-851b953d5465" />

Verify Cluster
<img width="1906" height="310" alt="image" src="https://github.com/user-attachments/assets/5ed89c07-2d52-4e1e-a04f-f776c27d764f" />

Pull docker images 
<img width="1906" height="398" alt="image" src="https://github.com/user-attachments/assets/070e2036-fb7f-48ec-bf7f-858e67651581" />

Create deployment.yaml file and service.yaml file
<img width="1902" height="827" alt="image" src="https://github.com/user-attachments/assets/d08cd41f-b127-47c9-aab6-df1d345f071a" />
<img width="1917" height="727" alt="image" src="https://github.com/user-attachments/assets/76edc14b-2148-4bc9-bc75-d1c1510c8ec7" />


Apply the Deployment check the pods

<img width="1906" height="136" alt="image" src="https://github.com/user-attachments/assets/1c27db72-0414-49dd-8b51-78a2ad6c8969" />

Apply the services and check service
<img width="952" height="131" alt="image" src="https://github.com/user-attachments/assets/79b35b8c-f959-427e-b0d1-839a17f66b3c" />

Verify by opening external ip in browser
<img width="1912" height="783" alt="image" src="https://github.com/user-attachments/assets/19378668-049f-4363-b59c-8dab2c447a7f" />

Create the deployment and service yaml file in ec2 change the remote to own github url and push
<img width="1916" height="391" alt="image" src="https://github.com/user-attachments/assets/70bebb75-d9cf-48dc-871b-e2e6feefdef4" />
<img width="1432" height="730" alt="image" src="https://github.com/user-attachments/assets/64654adb-b36e-461a-bd9b-2fdd50952273" />

Create buildspec.yml and push to git
<img width="1913" height="667" alt="image" src="https://github.com/user-attachments/assets/739173e3-6008-43b2-aa9e-2e62ab5ba8eb" />
<img width="1913" height="576" alt="image" src="https://github.com/user-attachments/assets/cf4f74c0-3831-4448-b01e-616082fa78d4" />

Create an IAM Role for CodeBuild AmazonEC2ContainerRegistryFullAccess,AmazonEKSClusterPolicy,CloudWatchLogsFullAccess,AmazonS3ReadOnlyAccess
<img width="1906" height="730" alt="image" src="https://github.com/user-attachments/assets/62724b2a-2f8d-4379-bf41-cfad1eafd23e" />
<img width="1876" height="793" alt="image" src="https://github.com/user-attachments/assets/679db77c-91a2-45d8-ac85-2c62a083ae6e" />

Create a CodeBuild Project 
<img width="1883" height="840" alt="image" src="https://github.com/user-attachments/assets/de163a05-6c2f-4fda-b996-689cb30da9db" />
<img width="1897" height="837" alt="image" src="https://github.com/user-attachments/assets/09a75a66-6d9a-4b2d-b4b0-0a258168a69f" />
<img width="1335" height="66" alt="image" src="https://github.com/user-attachments/assets/3d043755-e112-4135-a438-a40cd90e478d" />
<img width="1506" height="696" alt="image" src="https://github.com/user-attachments/assets/370bc2bb-a378-42cd-9ea1-4e32a91ecce9" />
<img width="1903" height="788" alt="image" src="https://github.com/user-attachments/assets/f8bba60c-4110-4e46-9b39-792cdc646f66" />

Add Docker Hub Credentials in envbiromwent variable 
<img width="1660" height="482" alt="image" src="https://github.com/user-attachments/assets/2c0534e2-71e5-4e95-bbff-03dac9b886cd" />

Start a Build
<img width="1901" height="808" alt="image" src="https://github.com/user-attachments/assets/ece8772d-8077-4b52-8094-6f25ec58f6ee" />

Create CodePipeline
<img width="1898" height="802" alt="image" src="https://github.com/user-attachments/assets/a933eb92-0173-4a97-b90e-5219b4ddbb3c" />

Pipeline Settings

<img width="1878" height="795" alt="image" src="https://github.com/user-attachments/assets/a626ef57-2982-428f-93ea-43f09596d6e2" />

Code Pipeline

<img width="1230" height="717" alt="image" src="https://github.com/user-attachments/assets/53665cb0-af01-4036-9ee7-20231e13cd49" />
<img width="1893" height="713" alt="image" src="https://github.com/user-attachments/assets/6d8a4b41-7d16-4f51-b29d-03eacc1ee1ab" />
<img width="1091" height="115" alt="image" src="https://github.com/user-attachments/assets/062bb22c-7e94-4195-9585-9a8e9450fe1c" />
<img width="1902" height="822" alt="image" src="https://github.com/user-attachments/assets/ef20273d-bb85-4233-b3eb-398830408051" />


Monitoring: Use CloudWatch Logs to track build, deploy

<img width="1872" height="866" alt="image" src="https://github.com/user-attachments/assets/b408f8ee-2da7-4fd5-acec-3e63297716b7" />
<img width="1547" height="713" alt="image" src="https://github.com/user-attachments/assets/8c0fd17d-6e2f-4d4e-b426-69afeb8e20f1" />

Application Logs

install the CloudWatch Observability add-on and verify
<img width="1066" height="412" alt="image" src="https://github.com/user-attachments/assets/4094b6b5-5dce-4a60-bea2-01f71cdd664f" />
<img width="1021" height="153" alt="image" src="https://github.com/user-attachments/assets/02d6b9b1-ffc5-4d32-9db9-4f6e95a076d6" />
<img width="1300" height="105" alt="image" src="https://github.com/user-attachments/assets/6d3ed56a-4723-4b37-9cfb-34c182d66c7f" />

App logs 

<img width="1748" height="196" alt="image" src="https://github.com/user-attachments/assets/0c0fb9ed-cdb2-46ba-8256-dadf0abb7027" />
<img width="1866" height="813" alt="image" src="https://github.com/user-attachments/assets/ed396143-8447-4e26-b9f5-75b57e6c3299" />
<img width="1657" height="625" alt="image" src="https://github.com/user-attachments/assets/00c64f77-466f-4ae7-b131-836ffa6c4e82" />
<img width="1737" height="762" alt="image" src="https://github.com/user-attachments/assets/aaed3db0-e121-4e15-99c2-0d5539460fd7" />
<img width="1677" height="653" alt="image" src="https://github.com/user-attachments/assets/319d0767-7348-4e3c-8806-1e36cd1b449f" />






