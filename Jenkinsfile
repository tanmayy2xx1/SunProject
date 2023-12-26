pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'master', url: 'https://tanmayy2xx1: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@github.com/tanmayy2xx1/SunProject.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_kdCg8GisGtHc7gyoaCguzj2H6iE | /usr/bin/docker login -u tanmay8180 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker image build -t tanmay8180/myproject .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push tanmay8180/myproject'
            }
        }
	stage ('docker remove service') {
	     steps {
		sh '/usr/bin/docker service rm myservice'
	    }
	}
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --replicas 5 --name myservice -p 8080:80 tanmay8180/myproject'
            }
        }
    }
} 
