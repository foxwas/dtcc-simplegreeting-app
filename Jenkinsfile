node{

	stage ("Checkout SimpleGreeting"){
        git branch: 'main', url: ' https://github.com/foxwas/dtcc-simplegreeting-app.git'
    }
    
    stage ("Maven Build - SimpleGreeting - Clean") {
        bat 'mvn clean'
    }
    
    stage ("Maven Build - SimpleGreeting - Build") {
        bat 'mvn package'
    }
	
	stage ("Maven Build - SimpleGreeting - Test") {
        bat 'mvn test'
    }

	stage('User Acceptance Test - SimpleGreeting') {
	
	  def response= input message: 'Is this build good to go?',
	   parameters: [choice(choices: 'Yes\nNo', 
	   description: '', name: 'Pass')]
	
	  if(response=="Yes") {
	    stage('Deploy App - SimpleGreeting') {
	      bat 'mvn verify'
	    }
	  }
    }
}