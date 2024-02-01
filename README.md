1) To create eks cluster using terraform , cd into direcotry eks-terraform and run command 
terraform apply -var="eks_nodes_desired_size=2" , this can be changed a per requirement.

2) The express directory contains the Dockerfile ,  we will copy the Dockerfile to directory containing code  we can build the docker image by using  docker build -t public.ecr.aws/l7l7a2r1/images:node 

3) We will deploy the express app  using command kubectl apply -f node-eks.yaml.

4) For the go app , we will copy the Dockerfile directory containing code , we can build the docker image by 
cd into go directory using 
docker build -t public.ecr.aws/l7l7a2r1/images:go.

5) We will deploy the go app  using command  kubectl apply -f go-eks.yaml.

6) Both go and express app are exposed via lb service in eks.  We can  do the benchmarking by hiting the lb service .
7) I benchmark express app using ab -n 1000 -c 50 http://a153ce61e7b304d288625303c8190222-2141567733.ap-south-1.elb.amazonaws.com:4001/api/benchmarks
8) I tested  go app using ab -n 1000 -c 50 http://af4cd0e3e0ee24fd9a10d5ab6f04c780-1747749285.ap-south-1.elb.amazonaws.com:8080/api/benchmarks
   


    
  

