def repo="https://github.com/sree77hari/sample-helm-chart"
pipeline{
		agent{
			label 'helm'
		}
		stages{
				
                stage("add Repo") {
                        steps {
                               sh "helm repo add sree77hari ${repo}"
                            }
                    }
				stage("Deploy to Dev") {
                        steps {
                            script{
					openshift.withCluster(){
                                        sh "helm upgrade --install helm-app sree77hari/sample-app --values dev/values.yaml -n dev --wait"
                                    }
                                }
                            }
                    }
                stage("Deploy to UAT") {
                        steps {
                            script{
					openshift.withCluster(){
                                        sh "helm upgrade --install helm-app sree77hari/sample-app --values uat/values.yaml -n uat --wait"
                                    }
                                }
                            }
                    }
            }
        }
