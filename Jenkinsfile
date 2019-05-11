Pipeline {
	any node
		stages{
			stage ('scm checkout'){
			git 'https://github.com/vivekdhake/maven-project.git'
			}
			
			stage ('compile stage'){
				steps{ 
				withmaven (maven: 'LocalMaven'){
				sh 'mvn compile'
			   }
			  }
			 }
			 
			 stage ('testing stage'){
			  steps{ 
			  withmaven (maven: 'LocalMaven'){
			  sh 'mvn test'
			   }
			  }	   
			 } 
			 
			  stage ('package stage'){
				steps {
					withmaven (maven: 'LocalMaven')
					sh 'mvn package'
					}
				}
			}
			 
			 stage ('install stage'){
				steps {
					withmaven (maven: 'LocalMaven'){
					sh 'mvn install'
					}
				}
			 }
			 
			
		}
	}
