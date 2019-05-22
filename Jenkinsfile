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
import java.nio.file.*
def destination = "/var/jenkins_home/workspace/Prueba_deploy"
def path = "/var/jenkins_home/workspace/unicoarchivos"
def branch_name = "clon-master2"
def proyecto = "Unico"
def earName = "unico.ear"			//Modificar segun el nombre del ear.
def tipo = "EAR1"					//Modificar segun el tipo de artefacto en mayusculas, las opciones son: EAR - JASPER - XML - JAR.


pipeline {
	agent any
	   	environment {

		SCM_URL = "https://github.com/nazpot01/Pruebas.git"
	        SCM_CREDENTIALS = "123456789"
		SCM_BRANCH = "*/${branch_name}"
		}
		
	stages {

		stage('test') {
                steps {
                    echo "[EXEC] - Obtener código fuente desde repositorio Git"
				}
			}
		stage('copiado'){
		steps {
			sh"pwd"
			sh"git checkout origin/clon-master2"
			sh"git diff --name-only origin/master | while read -r line; do cp \${line} /var/jenkins_home/workspace/unicoarchivos ; done"
			}
		
		}
		stage('Publisher'){
		steps {
			class FilesHelp {
			    def main() {
				def folder = new File("C:/Users/hhernanc/Desktop/HOLMAN/LABORATORIOS/DOCKER/DOCKER2")
				Arrays.asList(folder.listFiles()).stream().map(File::getAbsolutePath).filter(f -> f.toLowerCase().endsWith(".ear")).forEach(f -> processFile(new File(f))) 
			    }
					def processFile(def file) {
						Path copyDir = Paths.get("/var/jenkins_home/workspace/Prueba_deploy")
						Path originalPath = file.toPath()
						Path copyFile = copyDir.resolve(file.getName())
						if(!Files.exists(copyFile)) {
							Files.createFile(copyFile)
						}
						Files.copy(originalPath, copyFile, StandardCopyOption.REPLACE_EXISTING)
						
						System.out.println(originalPath)
						System.out.println(copyFile)
					}
				}
				new FilesHelp().main()
			}
		}
		
	}
}
