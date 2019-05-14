#!groovy
def pushProperties
def log
def tokens
def fileIncludePatterns = ''
def deploy = 0
def componentName
def componentTag
def componentAppName
def binder
def proyecto = "Unico"
def earName = "unico.ear"			//Modificar segun el nombre del ear.
def tipo = "EAR1"					//Modificar segun el tipo de artefacto en mayusculas, las opciones son: EAR - JASPER - XML - JAR.
									//Escoger las siguientes opciones para compilar EAR:	EAR1 = unico.ear
											//	EAR2 = UnicoAxis.ear
											//	EAR3 = AdminWeb.ear
											//	EAR4 = AdminSAT.ear
											//	EAR5 = InfoPro.ear
											//	EAR6 = EjecucionComandosWeb.ear
											//	EAR7 = bea-proxy.ear
pipeline {

	  agent any

    		tools {
        	maven 'Maven 3.5.2'
    }
	   	environment {

		SCM_URL = "https://devops-github.ath.net/unico/UnicoM.git"
		COMPONENT_APP = "UNICO MANTENIMIENTO"
	     	SCM_CREDENTIALS = "GitHub token ugithub"
		}

    stages {

    	stage('GET_CODE') {
        	steps {
			step([$class: 'WsCleanup'])
			echo "[EXEC] - Obtener código fuente desde repositorio Git"
			checkout([
				$class                           : 'GitSCM',
				branches                         : [
					[name: "*/${params.BRANCH}"]
				],
				doGenerateSubmoduleConfigurations: false,
				extensions                       : [],
				submoduleCfg                     : [],
				userRemoteConfigs                : [
					[credentialsId: "${SCM_CREDENTIALS}", url: "${SCM_URL}"]
				]
			])

				echo 'commit ok'
			script {

				switch (tipo) {
					case "EAR1":
						componentTag = "EAR"
						componentAppName = "Unico"			//Modificar segun el nombre del componente en Urbancode, se contemplan para desplegar (Unico - UNICO JAR - UNICO XML - UNICO JASPER).
						earName = "Unico.ear"				//Solo modificar en caso de que el artefacto a desplegar sea un Ear, de acuerdo con el componente a desplegar.
						binder = "ear"					//Modificar segun la carpeta creada con el nombre del artefacto en el repositorio Github.
					break
					case "EAR2":
						componentTag = "EAR"
						componentAppName = "UnicoAxis"			//Modificar segun el nombre del componente en Urbancode, se contemplan para desplegar (Unico - UNICO JAR - UNICO XML - UNICO JASPER).
						earName = "UnicoAxis.ear"			//Solo modificar en caso de que el artefacto a desplegar sea un Ear, de acuerdo con el componente a desplegar.
						binder = "ear"					//Modificar segun la carpeta creada con el nombre del artefacto en el repositorio Github.
					break
					case "EAR3":
						componentTag = "EAR"
						componentAppName = "AdminWeb"			//Modificar segun el nombre del componente en Urbancode, se contemplan para desplegar (Unico - UNICO JAR - UNICO XML - UNICO JASPER).
						earName = "AdminWeb.ear"			//Solo modificar en caso de que el artefacto a desplegar sea un Ear, de acuerdo con el componente a desplegar.
						binder = "ear"					//Modificar segun la carpeta creada con el nombre del artefacto en el repositorio Github.
					break
					case "EAR4":
						componentTag = "EAR"
						componentAppName = "AdminSAT"			//Modificar segun el nombre del componente en Urbancode, se contemplan para desplegar (Unico - UNICO JAR - UNICO XML - UNICO JASPER).
						earName = "AdminSAT.ear"			//Solo modificar en caso de que el artefacto a desplegar sea un Ear, de acuerdo con el componente a desplegar.
						binder = "ear"					//Modificar segun la carpeta creada con el nombre del artefacto en el repositorio Github.
					break
					case "EAR5":
						componentTag = "EAR"
						componentAppName = "InfoPro"			//Modificar segun el nombre del componente en Urbancode, se contemplan para desplegar (Unico - UNICO JAR - UNICO XML - UNICO JASPER).
						earName = "InfoPro.ear"				//Solo modificar en caso de que el artefacto a desplegar sea un Ear, de acuerdo con el componente a desplegar.
						binder = "ear"					//Modificar segun la carpeta creada con el nombre del artefacto en el repositorio Github.
					break
					case "EAR6":
						componentTag = "EAR"
						componentAppName = "EjecucionComandosWeb"	//Modificar segun el nombre del componente en Urbancode, se contemplan para desplegar (Unico - UNICO JAR - UNICO XML - UNICO JASPER).
						earName = "EjecucionComandosWeb.ear"		//Solo modificar en caso de que el artefacto a desplegar sea un Ear, de acuerdo con el componente a desplegar.
						binder = "ear"					//Modificar segun la carpeta creada con el nombre del artefacto en el repositorio Github.
					break
					case "EAR7":
						componentTag = "EAR"
						componentAppName = "bea-proxy"			//Modificar segun el nombre del componente en Urbancode, se contemplan para desplegar (Unico - UNICO JAR - UNICO XML - UNICO JASPER).
						earName = "bea-proxy.ear"			//Solo modificar en caso de que el artefacto a desplegar sea un Ear, de acuerdo con el componente a desplegar.
						binder = "ear"					//Modificar segun la carpeta creada con el nombre del artefacto en el repositorio Github.
					break
					case "JAR":
						componentTag = "JAR"				//Etiqueta de componente en urbancode, se contemplan (JAR - JASPER - XML) las siguientes:
						componentAppName = "UNICO JAR"			//Modificar segun el nombre del componente en Urbancode, se contemplan para desplegar (Unico - UNICO JAR - UNICO XML - UNICO JASPER).
						binder = "jar"					//Modificar segun la carpeta creada con el nombre del artefacto en el repositorio Github.
					break
					case "JASPER":
						componentTag = "JASPER"				//Etiqueta de componente en urbancode, se contemplan (JAR - JASPER - XML) las siguientes:
						componentAppName = "UNICO JASPER"		//Modificar segun el nombre del componente en Urbancode, se contemplan para desplegar (Unico - UNICO JAR - UNICO XML - UNICO JASPER).
						binder = "jasper"				//Modificar segun la carpeta creada con el nombre del artefacto en el repositorio Github.
					break
					case "XML":
						componentTag = "XML"				//Etiqueta de componente en urbancode, se contemplan (JAR - JASPER - XML) las siguientes:
						componentAppName = "UNICO XML"			//Modificar segun el nombre del componente en Urbancode, se contemplan para desplegar (Unico - UNICO JAR - UNICO XML - UNICO JASPER).
						binder = "xml"					//Modificar segun la carpeta creada con el nombre del artefacto en el repositorio Github.
					break
				}

				def actionDeploy = 0
				echo 'message commit validation'

				log = sh(returnStdout: true, script: "git log -1 | grep " + binder + " || true")
				echo 'logger->' + log + '|'

				if (log != null && log != ''){
					sh('ls *')
					actionDeploy = 1
				}
				if (tipo == "EAR"){
					fileIncludePatterns = proyecto + "/Artefactos/" + binder + "/" + earName
				} else {
				fileIncludePatterns = proyecto + "/Artefactos/" + binder + "/**/*"
				}

				pushProperties = 'BINDER=' + binder
				pushProperties = pushProperties + '\nCOMPONENT_NAME=' + componentAppName
				pushProperties = pushProperties + '\nPROYECTO=' + proyecto

				echo '' + "${COMPONENT_APP}"
				echo fileIncludePatterns
				echo pushProperties
				upload = 1
			}
		}
	}

	stage('UPLOAD_COMPONENTS') {
		steps {
			script {
				if (upload == 1) {
					componentName : componentAppName
					step([$class   : 'UCDeployPublisher',
						siteName : "${URBAN_PRD_APP}",
						component: [
							$class		: 'com.urbancode.jenkins.plugins.ucdeploy.VersionHelper$VersionBlock',
							componentName	: componentAppName,
							componentTag	: componentTag,
							createComponent: [
								$class		: 'com.urbancode.jenkins.plugins.ucdeploy.ComponentHelper$CreateComponentBlock',
								componentApplication: "${COMPONENT_APP}"
							],
							delivery       : [
								$class             : 'com.urbancode.jenkins.plugins.ucdeploy.DeliveryHelper$Push',
								pushVersion        : "${BUILD_ID}",
								baseDir            : "${WORKSPACE}",
								fileIncludePatterns: fileIncludePatterns,
								fileExcludePatterns: '',
								pushProperties     : pushProperties,
								pushDescription    : 'Entrega de artefactos'
							]
						]
					])
					deploy = 1;
				}
			}
		}
	}
}
	post {
		success {
			script {
				try {
					emailext(attachLog: true,
						subject: "SUCCESSFUL: Job ${env.JOB_NAME} - " + componentName + " Version: ${env.BUILD_NUMBER}",
						to: "prv_hhernandezcarde@ath.com.co",
						body: """<p>SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
						<p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${
							env.BUILD_NUMBER
						}]</a>&QUOT;</p>""",
						recipientProviders: [[$class: 'DevelopersRecipientProvider']])
				} catch (e) {
					emailext(attachLog: true,
						subject: "SUCCESSFUL: Job ${env.JOB_NAME} - " + componentName + " Version: ${env.BUILD_NUMBER}",
						to: "prv_hhernandezcarde@ath.com.co",
						body: """<p>SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
						<p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${
							env.BUILD_NUMBER
						}]</a>&QUOT;</p>""",
						recipientProviders: [[$class: 'DevelopersRecipientProvider']])
				}
			}
		}


		failure {
			script {
				try {
					emailext(attachLog: true,
		    subject: "FAILED: Job ${env.JOB_NAME} - " + componentName + " Version: ${env.BUILD_NUMBER}",
		    to: "prv_hhernandezcarde@ath.com.co",
		    body: """<p>FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
						<p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${
			env.BUILD_NUMBER
		    }]</a>&QUOT;</p>""",
		    recipientProviders: [[$class: 'DevelopersRecipientProvider']])
				} catch (e) {
					emailext(attachLog: true,
		    subject: "FAILED: Job ${env.JOB_NAME} - " + componentName + " Version: ${env.BUILD_NUMBER}",
		    to: "prv_hhernandezcarde@ath.com.co",
		    body: """<p>FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
						<p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${
			env.BUILD_NUMBER
		    }]</a>&QUOT;</p>""",
		    recipientProviders: [[$class: 'DevelopersRecipientProvider']])
			}
		     }
		}
	}
}

