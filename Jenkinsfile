pipeline { 
    agent any

    stages {
        stage('Git Checkout') {
            steps {
               git 'https://github.com/Johnjosh11/hello-world-1'
           }
        }
        stage('Checking the Current PWD') {
            steps {
                sh 'ls'
            }
        }
        stage('Clean and build, test, package') {
           steps {
              sh 'mvn clean'
           }
       }
        stage('Test') {
           steps {
            sh  'mvn test'
            }
        }
        stage('package') {
           steps {
            sh  'mvn package'
            }
        }
        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://13.58.41.200:8080/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
