def dockerImage;

node('docker'){
	stage('SCM'){
		checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/Echochris234/JenkinsDocker']]]);
	}
	stage('build'){
		dockerImage = docker.build('christianavargas/agent-dnc:v1', './dotnetcore');
	}
	stage('push'){
		docker login -u $dockerhub_USR --password-stdin
		docker push dockerImage
	}
}
