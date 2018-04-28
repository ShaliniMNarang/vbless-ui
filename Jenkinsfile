pipeline {
    agent any
    
    parameters {
        string(name: 'app', defaultValue: 'vblessimg/vbless-ui', description: 'vbless ui docker image')
    }

    stages {
        stage('Build') {
            steps {
            		sh '''
                 docker build -t vbless-ui .
                 docker tag vbless-ui chidanandapati/vbless-ui;
                 docker push chidanandapati/vbless-ui;
                 '''
            }
        }
        stage('Test') {
            steps {
                sh '''
                pwd
                ls
                echo "testing successful";
                '''
            }
        }
        stage('Deploy') {
            steps {
                sh '''
                kubect apply -f ui-deployment.yaml
                kubect apply -f ui-service.yaml
                '''
            }
        }
    }
}