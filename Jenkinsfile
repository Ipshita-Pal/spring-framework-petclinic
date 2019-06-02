node {
   
   stage('GITCODE'){
      git credentialsId: 'GIT', url: 'https://github.com/Ipshita-Pal/spring-framework-petclinic.git'
   }
  
  stage('JAVABUILD'){
     sh label: '', script: 'mvn clean install' 
  }

    stage('DOCIMAGE'){
    sh label: '', script: 'docker build -t ipshita/petclinic:v1 .'

}

    stage('DOCPUSH'){
    //withCredentials([usernamePassword(credentialsId: 'DOC', passwordVariable: 'pwd', usernameVariable: 'user')])
    withCredentials([usernamePassword(credentialsId: 'DOC', passwordVariable: 'pwd', usernameVariable: 'user')])
    {
     sh "docker login -u $user -p $pwd"
    }
     
     sh 'docker push ipshita/petclinic:v1'
}
}
