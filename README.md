
# jenkins-kops
This read me is for my reference in case I need to recreate 
A test for deploying jenkins on k8s
Pretty much followed 
https://www.blazemeter.com/blog/how-to-setup-scalable-jenkins-on-top-of-a-kubernetes-cluster

but for aws
1)Created Kops cluster  
2)For service used load balancer type
3)Make sure the security groups of load balancer and vpc
4) Create an alias record for the hosting zone of the domain

Pre req(Followd udemy  and https://kubernetes.io/docs/getting-started-guides/kops/)
1)Used vagrant 
2)Installed pre reqs like kops installation,python pip(for aws cli),kubectl install 
3)configured aws cli with access keys
4)ssh key gen to login to cluster
5)s3 bucket creation for kops state
6)cluster config
	kops create cluster --name=jenkins-k8s.hvk12.org --state=s3://jenkinshvk-k8s-state-store --zones=eu-west-2b --node-count=2 --node-size=t2.micro --master-size=t2.micro --dns-zone=hvk12.org
	export KOPS_STATE_STORE=s3://jenkinshvk-k8s-state-store
	kops update cluster jenkins-k8s.hvk12.org --yes
7)For getting the UI(dashboard of k8s)
	https://api.jenkins-k8s.hvk12.org/ui
	to skip the token auth get the yml from(https://github.com/kubernetes/dashboard/wiki/Access-control) check 'Admin privileges' section (this is just for testing purpose)
