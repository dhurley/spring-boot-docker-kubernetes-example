node {
    stage('Configure') {
        env.PATH = "${tool 'maven-3.3.9'}/bin:${env.PATH}"
        version = '1.0.' + env.BUILD_NUMBER
        currentBuild.displayName = version

        properties([
                buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '10')),
                disableConcurrentBuilds(), [$class: 'GithubProjectProperty', displayName: '',
                projectUrlStr: 'https://github.com/dhurley/spring-boot-docker-kubernetes-example.git/'],
                pipelineTriggers([])])
    }

    stage('Checkout'){
        git 'https://github.com/dhurley/spring-boot-docker-kubernetes-example.git'
    }

    stage('Build Image') {
        sh 'mvn clean package docker:build'
    }

    stage('Archive unit tests') {
        junit 'reports/**/*.xml'
    }
}