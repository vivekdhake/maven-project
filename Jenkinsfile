pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/vivekdhake/maven-project.git'
        }
  }
    {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn test'
                }
            }
        }


        stage ('install Stage') {
            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn install'
                }
            }
        }

         stage ('deploy to tomcat') {
            steps {
                sshagent(['e555f7aa-44f7-4460-a064-6d3fb0443fb9']) {
                sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@18.218.11.89:/var/lib/tomcat/webapps'
                }
            }
        }
        
         
}
}
