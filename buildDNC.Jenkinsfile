def dockerImage;


node('docker'){
	stage('SCM'){
		checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/Echochris234/JenkinsDocker']]]);
	}
	stage('build'){
		echo "${env.BUILD_NUMBER}"
		echo "${BUILD_NUMBER}"
		sh 'echo "$BUILD_NUMBER"'
		dockerImage = docker.build('christianavargas/agent-dnc:${BUILD_NUMBER}', './dotnetcore');
	}
	stage('push'){
		docker.withRegistry('','dockerhub_id'){
			dockerImage.push()
		}
	}
}
