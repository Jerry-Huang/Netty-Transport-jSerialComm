#!groovy
// Jenkinsfile (Pipeline Script)
node {
    stage('Checkout') {
        git url: scm.getUserRemoteConfigs()[0].getUrl()
    }

    withMaven(jdk: "jdk8", maven: "m3.5", mavenLocalRepo: ".repository") {

        stage('Build') {
            sh 'mvn clean compile'
        }

        stage('Test') {
            sh 'mvn test'
        }

        stage('Package') {
            sh 'mvn -DskipStatic -DskipTests install'
        }
    }
}