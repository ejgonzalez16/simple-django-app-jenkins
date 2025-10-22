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
                cp -r . /code/simple-django-app-jenkins
                cd /code/
                sudo docker-compose up -d --no-deps --build django-app
                '''
            }
        }
    }
}