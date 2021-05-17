pipeline {
  agent any
  tools {
    maven "Maven"
  }
    stages {
        stage('build') {
            steps {
                echo 'build ...'
                sleep 5
            }
        }
        stage('test') {
            steps {
                echo 'test ..'
            }
        }
        stage('Deploy for development') {
            when {
                branch 'Dev'
            }
            steps {
                 echo 'dev branch deployment ...'
              sleep 5
             snDevOpsArtifact(artifactsPayload:"""{"artifacts": [{"name": "development_artifact.jar","version": "1.1","semanticVersion": "1.1.0","repositoryName": "Test"}],"stageName": "Deploy for development"}""")
                
            }
        }
        stage('Deploy for production') {
            when {
                branch 'Prod'  
            }
            steps {
                echo 'prod branch deployment .'
             snDevOpsArtifact(artifactsPayload:"""{"artifacts": [{"name": "prod_artifact.jar","version": "1.1","semanticVersion": "1.1.0","repositoryName": "prod_artifact_repo"}],"stageName": "Deploy for production"}""")
                sleep 5
            }
        }
    }
}
