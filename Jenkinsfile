pipeline {
    agent any
    stages {
        stage('clone'){
            steps {
                    git (
                        branch: 'main', 
                        url: "https://github.com/ejgonzalez16/simple-django-app-jenkins"
                    )
                } 
        }
        stage('pylint') {
            steps {
                sh'''
	            pylint cool_counters/counter || true
                pylint cool_counters/counter/migrations || true
                pylint cool_counters/cool_counters || true
                '''
            }
        }
        stage('run-docker') {
            steps {
                sh'''
                cp -r . /var/jenkins_home/simple-django-app-jenkins
                cd /var/jenkins_home
                sudo docker compose up -d --build django-app
                '''
            }
        }
    }
}