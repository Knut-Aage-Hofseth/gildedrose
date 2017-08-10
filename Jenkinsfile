node {
   stage ('Preparation') {
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'af8e255b-7254-4a6c-8ac3-4b4d27af818e', url: 'git@github.com:Knut-Aage-Hofseth/gildedrose.git']]])
   }
   
   stage ('Build'){
       sh 'docker run -i --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn install'
   }
   
   stage ('Results'){
       junit '**/target/surefire-reports/TEST-*.xml'
       archiveArtifacts 'target/gildedrose-*.jar'

   }
}
