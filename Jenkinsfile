node {
    
    def maven_path = tool (name: 'maven', type: 'maven') + '/bin/mvn'
    
    stage('checkout')
    
    {
    git 'https://github.com/Mahesh515/demo.git'
    }
    
    stage('compile-test')
    
    {
        sh "${maven_path} compile test"
        
        
    }
    
    stage('package')
    
    {
        
        sh "${maven_path} package"
    }
    
    stage('static code analysis')
    
    {
        
        sh "${maven_path} pmd:pmd"
    }
    
    stage("publish test results")
    
    {
        realtimeJUnit('target/surefire-reports/*.xml') {
  
}

   stage("static code analysis")
   
   {
       
       recordIssues(tools: [pmdParser(pattern: '**/target/pmd.xml')])
   }
    }
}
