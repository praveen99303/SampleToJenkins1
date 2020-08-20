#!groovy

pipeline {
    agent any

    stages {
        stage('Source'){
	 steps{
	   echo 'DOWNLOADING SOURCE START'
	   checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'MyPrivateGit-APG', url: 'https://github.com/praveen99303/SampleToJenkins1.git/']]])
	   echo 'DOWNLOADING SOURCE COMPLETED'
	 }
	}
        stage('Build') {
            steps {
		echo 'BUILD STARTING...'
                bat "\"${tool 'MSBuild'}\" SampleToJenkins1.sln /p:DeployOnBuild=true /p:DeployDefaultTarget=WebPublish /p:WebPublishMethod=FileSystem /p:SkipInvalidConfigurations=true /t:build /p:Configuration=Release /p:Platform=\"Any CPU\" /p:DeleteExistingFiles=True /p:publishUrl=c:\\inetpub\\wwwroot"
                echo 'BUILD COMPLETED'
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
