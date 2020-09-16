pipeline {
	agent any
	stages {

		stage('Create kubernetes cluster') {
			steps {
				withAWS(region:'us-east-1', credentials:'capstone') {
					sh '''
						eksctl create cluster \
						--name capstonecluster \
						--version 1.17 \
						--nodegroup-name standard-workers \
						--node-type t2.small \
						--nodes 2 \
						--nodes-min 1 \
						--nodes-max 3 \
						--node-ami auto \
						--region us-east-1 \
					'''
				}
			}
		}

		

		stage('Create conf file cluster') {
			steps {
				withAWS(region:'us-east-1', credentials:'capstone') {
					sh '''
						aws eks --region us-east-1 update-kubeconfig --name capstonecluster
					'''
				}
			}
		}

	}
}

