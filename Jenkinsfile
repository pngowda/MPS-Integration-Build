node {
	stage ('checkout'){ 
		checkout scm 
    }
	stage ('build'){
		echo "Building on branch: ${env.BRANCH_NAME}"
		//if(isUnix()) {
		//	sh "./gradlew -b build.gradle publish"
		//}
		//else{
		//	bat "./gradlew -b build.gradle publish"
		//}
	}
        
	stage ('deploy'){
		echo "Deployment stage"
		withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: '<CREDENTIAL_ID>',
                    usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD']]) {bat ''' echo %USERNAME%'''}
	}
	
}
