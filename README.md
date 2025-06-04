[# dev](https://github.com/Akashmishra1421

https://github.com/Vinayak-Rajput

https://youtube.com/playlist?list=PL74ngi5StBW7xYwCNBPKmvGTPuFEV8WHv&si=kvj0VdGO0ytWZ_Pz

https://github.com/theashishshah

https://GitHub.com/rajayush808

GITHUB COMMANDS TO PUSH:

step 1: git init
step 2: git add .
step 3: git commit -m "first commit"
step 4: git branch -M main
step 5: git remote add origin "LINK"
step 6: git push -u origin main
step 7: give username and in password generate a token and paste it.


MAVEN(FIRST PROGRAM):

step 1: mvn archetype:generate -DgroupId=com.example -DartifactId=MyMavenApp -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
step 2: cd MyMavenApp
step 3: gedit pom.xml
step 4: mvn clean install
step 5: ls target/
step 6: java -jar target/MyMavenApp-1.0-SNAPSHOT.jar
step 7: gedit Jenkinsfile


GRADLE:

step 1: mkdir MyGradleApp
step 2: cd MyGradleApp
step 3: gradle init --type java-application
step 4: gedit build.gradle
step 5: gradle build
step 6: gradle run
step 7: gradle display


JENKINSFILE:

pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/theashishshah/final-maven.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Run Application') {
            steps {
                sh 'java -jar target/MyMavenApp-1.0-SNAPSHOT.jar'
            }
        }
    }
    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}


BUILD.GRADLE:

apply plugin: 'java'
repositories {
    jcenter()
}
dependencies {
    implementation 'com.google.guava:guava:23.0'
    testImplementation 'junit:junit:4.12'
}
mainClassName = 'App'


JENKINS:

Step 1: Go to localhost:8080→ Enter New Item name (e.g., maven)→ Select “Pipeline”→ Click OK
Step 2: Scroll to the Pipeline section→ Choose Pipeline Script select SCM→ Add github credentials→ change '/master' to '/main'→ Apply and save 
Step 3: Run the Pipeline→ Click “Build Now”


AZURE PIPELINE:

Step 1: Go to https://portal.azure.com/#home→ Click on 'Azure Devops Organization'→ Create new organization→ Name your project→ Private → Create
Step 2: Inside the project→ Click Pipelines→ Create Pipeline→ Select 'GitHub YAML'→ Authorize access→ Choose your repository→ Click on all repository
Step 3: Click on 'Starter pipeline'→ Update the pipeline YAML→ Click on save and run→ Click on view→ Allow permit 
Step 4: Go to Project Settings→ Agent Pools → Default → New Agents→ Click “Download Agent”→ Extract it→ Open Terminal:
                       mkdir mySelfHostedAgent
                       cd mySelfHostedAgent
		       ls
		       cd (copy the details from ls command)
                       ./config.sh
Step 5: Enter the Azure organization URL when prompted→ When asked for authentication, press Enter → Create a PAT (Personal Access Token):→ Go to User Settings → Personal Access Tokens → New Token
	•	Name: myPAT
	•	Expiry: 30 days
	•	Access: Full access → Create → Copy PAT
		Paste PAT in terminal when asked→ Press Enter for defaults (agent pool, work folder, agent name)→ Run the agent: ./run.sh→ Go to Azure and run pipeline and set branch as 'main' and run


MAVEN ANSIBLE(FIFTH PROGRAM):

step 1: mvn archetype:generate -DgroupId=com.example -DartifactId=MavenWebApp -DarchetypeArtifactId=maven-archetype-webapp -DinteractiveMode=false
step 2: cd MavenWebApp
step 3: gedit pom.xml
step 4: mvn clean install
step 5: mkdir ansible && cd ansible
step 6: gedit hosts.ini
step 7: gedit playbook.yml


WEBAPP ANSIBLE POM.XML:

<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>MavenWebApp</artifactId>
  <packaging>war</packaging>
  <version>1.0-SNAPSHOT</version>
  <name>MavenWebApp Maven Webapp</name>
  <url>http://maven.apache.org</url>
  <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>3.8.1</version>
      <scope>test</scope>
    </dependency>
    <dependency>
	<groupId>javax.servlet</groupId>
		<artifactId>javax.servlet-api</artifactId>
		<version>4.0.1</version>
		<scope>provided</scope>
	</dependency>
  </dependencies>
  <build>
  <plugins>
	<plugin>
	<groupId>org.apache.maven.plugins</groupId>
	<artifactId>maven-war-plugin</artifactId>
	<version>3.4.0</version>
	<!--  Update to latest stable version  -->
	</plugin>
	</plugins>
    <finalName>MavenWebApp</finalName>
  </build>
</project>


HOSTS.INI FOR ANSIBLE:

[web]
localhost ansible_connection=local ansible_python_interpreter=/usr/bin/python3


PLAYBOOK.YML FOR ANSIBLE:

- name: Deploy to Tomcat
  hosts: web
  become: yes
  tasks:
    - name: Copy WAR file to Tomcat
      copy:
        src: "/var/snap/jenkins/4870/workspace/MavenAnsible/target/MavenWebApp.war"
        dest: "/opt/tomcat/webapps/MavenWebApp.war"
        remote_src: no
    - name: Restart Tomcat
      systemd:
        name: tomcat
        state: restarted


YAML FILE FOR AZURE:

trigger:
- master

pool:
  name: Default

steps:
- script: echo My Gradle Application
  displayName: 'Run a one-line script'
- script: gradle build
  displayName: 'Building the gradle application'
- script: gradle run
  displayName: 'Running gradle application'

)
