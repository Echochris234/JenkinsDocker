def dockerImage;


node('docker'){
	stage('SCM'){
		checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/Echochris234/JenkinsDocker']]]);
	}
	stage('build'){
		dockerImage = docker.build('christianavargas/agent-dnc:v$BUILD_NUMBER', './dotnetcore');
	}
	stage('push'){
		docker.withRegistry('','dockerhub_id'){
			dockerImage.push()
		}
	}
}
