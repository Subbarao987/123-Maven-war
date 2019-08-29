pipeline {

  agent {label 'Master'}
  tools {
   maven "M2_HOME"
   jdk "java8"
  }
	  stages {
	  stage("cloning from git")
	  
	   {
		steps {
		echo "Am cloning from git"
		git credentialsId: '17e34f9d-4e06-473d-9185-46ef699a2a8f', url: 'https://github.com/Subbarao987/123-Maven-war.git'
		}
	 }
	  stage("Build using Maven") {
			
			steps {
		   echo "am using Maven "
		   bat(/"%MVN_HOME%\bin\mvn" -Dmaven.test.failure.ignore clean install/)
	  }
	}
	  stage("Deploy") {
			steps {
			echo "am using Deploy"
			deploy adapters: [tomcat8(credentialsId: '7e5721eb-ddb6-4c39-8baa-305ee7c3f325', path: '', url: '')], contextPath: null, war: '**/*war'
	  }
	}
	}
}
