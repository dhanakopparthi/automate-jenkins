pipeline {
 agent any

stages {
   stage("ci") {
   steps {
     sh 'zip -r helloworld.html-$BUILD_NUMBER.zip *'  
     sh 'aws s3 cp helloworld.html-$BUILD_NUMBER.zip s3://artifactory-html/'
   }
   }
   stage("cd"){
      steps {
      sh 'rm -fr *'
      sh 'aws s3 cp s3://artifactory-html/my-world.html-$BUILD_NUMBER.zip .'
      sh 'unzip my-world.html-$BUILD_NUMBER.zip' 
      sh 'scp my-world.html root@172.31.2.233:/var/www/html/'
   }
   }
}
}