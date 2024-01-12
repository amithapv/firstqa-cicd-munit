pipeline {

agent any

stages {

stage(‘Build Application’) {

steps {

bat ‘mvn clean install’

}

}

stage(‘Test’) {

steps {

echo ‘Application in Testing Phase…’

bat ‘mvn test’

}

}

stage(‘Deploy CloudHub’) {

environment {

ANYPOINT_CREDENTIALS = credentials(‘anypointPlatform’)

}

steps {

echo ‘Deploying mule project due to the latest code commit…’

echo ‘Deploying to the configured environment….’

bat ‘mvn package deploy -DmuleDeploy -Dusername=${ANYPOINT_CREDENTIALS_USR} -Dpassword=${ANYPOINT_CREDENTIALS_PSW} -DworkerType=Micro -Dworkers=1 -Dregion=us-west-2’

}

}

}

}

3. Configure the pom.xml with the below maven plugin under <build><plugins> tag

<plugin>

<groupId>org.mule.tools.maven</groupId>

<artifactId>mule-maven-plugin</artifactId>

<plugin>

<groupId>org.mule.tools.maven</groupId>

<artifactId>mule-maven-plugin</artifactId>

<version>${mule.maven.plugin.version}</version>

<extensions>true</extensions>

<configuration>

<cloudHubDeployment>

<uri>https://anypoint.mulesoft.com/</uri>

<muleVersion>${app.runtime}</muleVersion>

<username>${username}</username>

<password>${password}</password>

<applicationName>${project.artifactId}</applicationName>

<environment>Sandbox</environment>

<workerType>${workerType}</workerType>

<workers>1</workers>

<objectStoreV2>true</objectStoreV2>

<region> ${region} </region>

</cloudHubDeployment>

</configuration>

</plugin>
