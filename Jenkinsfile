pipeline {
    agent any
    
    stages {
        stage('Compile and Clean') { 
            steps {

                bat "mvn clean compile"
            }
        }
       
		
        
        stage('SonarQube'){
			steps{
				bat label: '', script: '''mvn sonar:sonar \
				-Dsonar.host.url=http://localhost:9000 \
				-Dsonar.login=squ_85162e2500772e6d7b2610e8d432c21134880252'''
			}
   		}
        
     

        stage('Build Docker image'){
            steps {
              
                bat 'docker image build -t spring-docker-jenkins-app1  .'
           }
        }

    //    stage('Docker Login'){
            
    //        steps {
    //             withCredentials([string(credentialsId: 'DockerId', variable: 'Dockerpwd')]) {
    //               bat "docker login -u aruna708 -p ${varthr708*}"
    //            }
    //        }                
        

  //      stage('Docker Push'){
   //         steps {
   //             bat 'docker push aruna708/spring-docker-jenkins-app1:latest'
   //         }
  //     }
        
        stage('Docker deploy'){
          steps {
               
              bat 'docker run -itd -p  8086:8086 aruna708/spring-docker-jenkins-app1:latest'
            }
        }

        
      
     
    }
}
