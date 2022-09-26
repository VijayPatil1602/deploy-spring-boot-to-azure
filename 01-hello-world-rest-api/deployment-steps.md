
### ---------------- Configure azure web app maven plugin

### -- add this plugin in your pom.xml in plugin section

###   <plugins>
###       <plugin>
###   		<groupId>com.microsoft.azure</groupId>
###   		<artifactId>azure-webapp-maven-plugin</artifactId>
###   		<version>1.7.0</version>
###   	</plugin>
###   </plugins>


1.   To configure maven plugin in pom.xml (azure maven plugin) (com.microsoft.azure)
2.   we need to run the above plugin 
3.   azure plugin hit the command like (azure-webapp:config)
4.   right click on project root folder
5.   select run maven ->  new goal -> in cammand line tyepe -> azure-webapp:config


### ----------------
OR   There is another way also like from cammand line
type 
cd the project root folder
    mvn azure-webapp:config

### ----------------
After hitting the azure-webapp:config command you can see the configuration in pom.xml
like version, resource group, app name, pricing tier, region, runtime configuration


        <configuration>
          <schemaVersion>V2</schemaVersion>
          <resourceGroup>hello-world-rest-api-rg</resourceGroup>
          <appName>hello-world-rest-api-wb-app-vijay</appName>
          <pricingTier>B1</pricingTier>
          <region>westeurope</region>
### ------- in order to set port as 8080 you need to add app setting with the property
### ------- JAVA_OPTS is the environment variable and
### ------- value is -Dserver.port = 80
### ------- with this your spring boot application will run on port 80
          <appSettings>
            <property>
              <name>JAVA_OPTS</name>
              <value>-Dserver.port=80</value>
            </property>
          </appSettings>
          <runtime>
            <os>linux</os>
            <javaVersion>jre8</javaVersion>
            <webContainer>jre8</webContainer>
          </runtime>
          <deployment>
            <resources>
              <resource>
                <directory>${project.basedir}/target</directory>
                <includes>
                  <include>*.jar</include>
                </includes>
              </resource>
            </resources>
          </deployment>
        </configuration>



### ------- when you want to deploy an application using the azure-web-app-maven-plugin,
### ------- the command to use is

### -------------   mvn azure-webapp:deploy --------------------

### --- before hitting the deploy cammand, login to the azure from powershell on windows
### --- it requires Azure CLI check out the README.MD file
### --- az --version -- to check the azure cli is installed or not in powershell
### --- az login --- to login into the azure into the local desktop

### --- now hit this command on terminal or powershell or cmd by going to the root path 
### --- of the project where pom.xml is present

### -------------   mvn azure-webapp:deploy --------------------








