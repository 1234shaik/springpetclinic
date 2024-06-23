pipeline {
    agent any
    stages {
        stage('SCM') {
            steps {
                git 'https://github.com/1234shaik/springpetclinic.git'
            }
        }
         stage('Maven Build') {
            steps {
                bat 'mvn clean package'
            }
        }
            
        
        stage('artifact_backup') {
            steps {
              script {
                def SERVER_ID = "artifactory"
                def server = Artifactory.server SERVER_ID
                def downloadSpec = """{
                  "files": [
                     {
                        "pattern": "spring-pet-frame/target*.war",
                        "target": "petclinc-dev/"
                     }
                  ]
               }"""
                server.upload(downloadSpec)
            }
        }
     } 
    }
}
