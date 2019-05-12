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


        stage ('package Stage') {
            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn package'
                }
            }
        }

        
        
       stage('build && SonarQube analysis') {
            steps {
                withSonarQubeEnv('sonar') {
                    // Optionally use a Maven environment you've configured already
                    withMaven(maven : 'LocalMaven') {
                        sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
        
         
}
}
