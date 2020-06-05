node{
   stage('SCM Checkout'){
     git credentialsId: 'Git', url: 'https://github.com/AishwaryaDevOps/hello-world.git'
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'M2', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
}
