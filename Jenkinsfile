pipeline {
    agent {
        docker {
            image 'maven:3.8.6-openjdk-8' 
            args '-u root -v /var/jenkins_home/.m2:/root/.m2' 
        }
    }
    options {
        skipStagesAfterUnstable()
        cache(maxCacheSize: 250, defaultBranch: 'master', caches: [arbitraryFileCache(path: '.ekstazi')]) 
    }
    stages {
        stage('CheckVersionJava') { 
            steps {
                sh 'java -version'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn ekstazi:ekstazi "-Drat.skip=true"'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo Deploy success.'
            }
        }
    }
}