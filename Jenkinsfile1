@Library('test') _

pipeline {
    agent {
        kubernetes {
            inheritFrom 'jenkins-agent'
        }
    }
    environment {
        //PowerVS specific variables
        POWERVS_REGION = "lon"
        POWERVS_ZONE = "lon06"
        VPCREGION= "eu-gb"
        JENKINS_TOKEN_DUMMY= "***REMOVED***"
	 }
	stages {
        stage('pull artifact') {
            steps {
                getArtifacts("mirror-openshift-release", "latest-${OCP_RELEASE}-build.txt" )
            }
        }
    }
}
