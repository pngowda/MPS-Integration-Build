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
		withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: '5adb1198-d66b-434a-aed1-56326f66567a',
                    usernameVariable: 'Username', passwordVariable: 'Password']]) {
					bat ''' echo %Username%''' %Password%}
	}
	
}
