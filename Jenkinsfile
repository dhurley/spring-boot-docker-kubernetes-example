node {
    stage('Configure') {
        env.PATH = "${tool 'maven-3.5.0'}/bin:${env.PATH}"
        version = '1.0.' + env.BUILD_NUMBER
        currentBuild.displayName = version
        tool name: 'docker-latest', type: 'org.jenkinsci.plugins.docker.commons.tools.DockerTool'

        properties([
                buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '10')),
                disableConcurrentBuilds(), [$class: 'GithubProjectProperty', displayName: '',
                projectUrlStr: 'https://github.com/dhurley/spring-boot-docker-kubernetes-example.git/'],
                pipelineTriggers([githubPush()])])
    }

    stage('Checkout'){
        checkout scm
    }

    stage('Docker') {
        def newApp = docker.build "djhurley/spring-boot-docker-kubernetes-example:0.0.1"
        newApp.push()
    }
}