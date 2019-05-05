pipeline {
    agent {
        kubernetes {
            label "automation-tests-slave"
            containerTemplate {
                name "k8s-slave-jdk12-alpine"
                image "openjdk:12-jdk-alpine"
                ttyEnabled true
                command 'cat'
            }
        }
    }
    stages {
        stage('Run Tests') {
            parallel {
                stage('First Build') {
                    build job: 'Experimental_Parameterized_Job',
                            parameters: [
                                    string(name: 'MVN_STRING', value: "First Build")
                            ]
                }
                stage('Second Build') {
                    build job: 'Experimental_Parameterized_Job',
                            parameters: [
                                    string(name: 'MVN_STRING', value: "Second Build")
                            ]
                }
                stage('Third Build') {
                    build job: 'Experimental_Parameterized_Job',
                            parameters: [
                                    string(name: 'MVN_STRING', value: "Third Build")
                            ]
                }
            }
        }
    }
}
