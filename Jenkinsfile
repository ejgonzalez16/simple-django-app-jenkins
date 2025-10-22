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
                pylint cool_counters
                '''
            }
        }
        stage('run-dockcer') {
            steps {
                ssh'''
                cp simple-django-appjenkins /var/jenkins_home/tmp
                cd /var/jenkins_home/tmp
                sudo docker compose up -d --build django-app
                '''
            }
        }
    }
}