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
                    steps {
                        build job: 'Parameterized_NodeJS_Test',
                                parameters: [
                                        string(name: 'INPUT_TEXT', 
                                                value: "'Hello First Build'")
                                ]
                    }
                }
                stage('Second Build') {
                    steps {
                        build job: 'Parameterized_NodeJS_Test',
                                parameters: [
                                        string(name: 'INPUT_TEXT', 
                                                value: "'Hello Second Build'")
                                ]
                    }
                }
                stage('Third Build') {
                    steps {
                        build job: 'Parameterized_NodeJS_Test',
                                parameters: [
                                        string(name: 'INPUT_TEXT', 
                                                value: "'Hello Third Build'")
                                ]
                    }
                }
                stage('Fourth Build') {
                    steps {
                        build job: 'Parameterized_NodeJS_Test',
                                parameters: [
                                        string(name: 'INPUT_TEXT',
                                                value: "'Hello Fourth Build'")
                                ]
                    }
                }
                stage('Fifth Build') {
                    steps {
                        build job: 'Parameterized_NodeJS_Test',
                                parameters: [
                                        string(name: 'INPUT_TEXT',
                                                value: "'Hello Fifth Build'")
                                ]
                    }
                }
            }
        }
    }
}
