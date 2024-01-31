1) To create eks cluster using terraform , cd into direcotry eks-terraform and run command 
terraform apply -var="eks_nodes_desired_size=2"
2) The express directory contains the Dockerfile we can build the docker image by cd into express directory using 
docker build -t public.ecr.aws/l7l7a2r1/images:node 
3) We will deploy the express app  using command kubectl apply -f node-eks.yaml.
4) 

