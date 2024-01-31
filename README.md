1) To create eks cluster using terraform , cd into direcotry eks-terraform and run command 
terraform apply -var="eks_nodes_desired_size=2" , this can be changed a per requirement.

2) The express directory contains the Dockerfile ,  we will copy the Dockerfile directory containing cod and  we can build the docker image by cd into express directory using  docker build -t public.ecr.aws/l7l7a2r1/images:node 

3) We will deploy the express app  using command kubectl apply -f node-eks.yaml.

4) For the go app , we will copy the Dockerfile directory containing code , we can build the docker image by cd into go directory using 
docker build -t public.ecr.aws/l7l7a2r1/images:go.

5) We will deploy the go app  using command kubectl apply -f go-eks.yaml.

6) Both go and express app are exposed via lb service in eks.  We can  do the benchmarking by hiting the lb service .
   


    
  

