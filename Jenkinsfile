node {
    stage ('Hello'){
        echo 'Hello World'
    }
    stage('Git'){
        git credentialsId: 'Jenkins SSH', url: 'git@github.com:JonathanKrogsager/gildedrose.git'

    }
    stage ('Test'){
        sh 'docker run -i --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn install'
    }
    stage ('Results'){
        archiveArtifacts '**/target/surefire-reports/TEST-*.xml'
    }
    stage('Javadoc'){
         sh 'docker run -i --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn site'
    }
    stage('Results2'){
        archiveArtifacts '**/target/site/'
    }
    stage('Results3'){
        archiveArtifacts '**/target/gildedrose-*.jar'
    }
}
