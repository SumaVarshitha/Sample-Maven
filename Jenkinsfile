@Library('shlib')_
pipeline {
	 
    agent any
  
    stages {
	    stage('clonestage'){
		    steps{
		  // sh 'rm -rf assessmentdocker' 
	        //sh 'git clone https://github.com/SumaVarshitha/Sample-Maven.git'
		    clonerepo()
		    }}
		 
        stage('build') {
            steps {
			  
                 //docker.image("sumavarshitha/java-maven-node").inside(){
                     // sh "mvn clean package"
                  // }
		    dockerbuild()
                }
			
            
	    }
        
        stage('SonarQube Analysis'){
		
		 environment{
               sonarscanner = tool 'sonars'
                   }
          steps{
           withSonarQubeEnv('sonar'){
                   // sh '${sonarscanner}/bin/sonar-scanner -Dproject.settings=./sonar-project.properties'
		     // sh "${scannerHome}/bin/sonar-scanner"
            sh "${sonarscanner}/bin/sonar-scanner -Dsonar.projectKey=SumaVarshitha_Sample-Maven -Dsonar.organization=sumavarshitha -Dsonar.projectName=Sample-Maven -Dsonar.projectVersion=1.0 -Dsonar.language=java -Dsonar.sources=src -Dsonar.java.binaries=. -Dsonar.host.url=https://sonarcloud.io/ -Dsonar.login=23c3c4a2d8cdc3f94ecc357df8d681a601cb48f6 -Dsonar.java.coveragePlugin=jacoco -Dsonar.sourceEncoding=UTF-8 -Dsonar.coverage.jacoco.xmlReportPaths=target/site/jacoco/jacoco.xml"
		    //sonarqube()
	       }
            }
       }

    
        
     /* stage("Quality Gate") {
            steps {
            // timeout(time: 3, unit: 'MINUTES') {
             //  waitForQualityGate abortPipeline: true
		    qualitygate()
             // }
           }
        }*/
    }
}
