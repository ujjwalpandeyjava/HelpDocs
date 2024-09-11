# Java helpful

### [How to use .md, click here.](https://guides.github.com/features/mastering-markdown/)


## 1. Remember:
In maven project all the stuff in build path has to be under classpath.





## 2. Could not initialize class org.apache.maven.plugin.war.util.WebappStructureSerializer
Reason:  It arises because, new eclipse need the "maven-war-plugin" to know which version it is and what class it want.

Solution: Add in pom.xml(full tag with data) 
<build>
	<plugins>
		<plugin>
			<groupId>org.apache.maven.plugins</groupId>
			<artifactId>maven-war-plugin</artifactId>
			<version>3.3.1</version>
		</plugin>
	</plugins>
	<finalName>ProjectName</finalName>
</build>






## 3. The superclass "jakarta.servlet.http.HttpServlet" was not found on the Java Build Path
Reason: - It is not able to get the server to hold the jsp and servlets

Solution:
	Add dependency for the "jakarta.servlet.http.HttpServlet
	<!-- java 17 -->
	<dependency>
		<groupId>jakarta.servlet</groupId>
		<artifactId>jakarta.servlet-api</artifactId>
		<version>6.0.0</version>
		<scope>provided</scope>
	</dependency>

	<!-- lower then java 17  -->
	<dependency>
		<groupId>javax.servlet</groupId>
		<artifactId>javax.servlet-api</artifactId>
		<version>4.0.1</version>
		<scope>provided</scope>
	</dependency>
	<dependency>
		<groupId>javax.servlet.jsp</groupId>
		<artifactId>javax.servlet.jsp-api</artifactId>
		<version>2.3.3</version>
		<scope>provided</scope>
	</dependency>





## 4. JAR WAR
https://www.baeldung.com/java-jar-war-packaging 





## 5. Versioning
	<properties>
		<java.version>17</java.version>
		<maven.compiler.source>17</maven.compiler.source>
		<maven.compiler.target>17</maven.compiler.target>
	</properties>
	
	
	

## 6. View page thymeLeaf
	Install plugin from here first in Eclipse/STS
	https://www.thymeleaf.org/eclipse-plugin-update-site/





## 7. Use Lombok
Install Lombok pc with: https://projectlombok.org/download
Install plugin:  https://projectlombok.org/p2




## 8. Note;
install software in eclipse to use
lombok -> https://projectlombok.org/p2
thymeLeaf -> https://raw.githubusercontent.com/thymeleaf/thymeleaf-extras-eclipse-plugin/update-site/3.1.0/



## 9. Referenced file contains errors (http://hibernate.sourceforge.net/hibernate-configuration-3.0.dtd). For more information, right click on the message in the Problems View and select
Reason: No need to connect this line after hibernate version 5
Solution:
<!-- <!DOCTYPE hibernate-configuration PUBLIC "-//Hibernate/Hibernate Configuration DTD//EN" "http://hibernate.sourceforge.net/hibernate-configuration-3.0.dtd"> -->

## 10. Keep the response structure:
	{
		"code": 0,	// The cod must be custom to the project
		"msg": "Success",
		"data": {
			"key": value
		},
		"success": true
	}



# Topic 2

## Similar search
commons text library in java for work to find similar string on base of score

## Stream
1. Find the distinct numbers:

		List<Integer> noOfTimes = arr.stream().filter(e -> Collections.frequency(arr, e) > 1).distinct().collect(Collectors.toList());

2. Find the no of Times occurrence.

		Map<Object, Long> noOfTimes = arr.stream().collect(Collectors.groupingBy(p -> p, Collectors.counting()));


# Folder File use

## Folders
1. META-INF: (manifest file) (to configure)

	The META-INF directory, if it exists, is used to store package and extension configuration data, including security, versioning, extension and services.


2. WEB-INF: (Deployment Descriptor)

	The WEB-INF directory contains the deployment descriptors for the Web application ( web.xml and weblogic.xml ) and two subdirectories for storing compiled Java classes and library JAR files. These subdirectories are respectively named classes and lib.
	
## Files
1. web.xml

	web.xml file is the deployment descriptor of the web application and contains a mapping for servlets (prior to 3.0), welcome pages, security configurations, session timeout settings, etc.




# Project now working

1. Must check
	a). Project facelets (java version, Dynamic web module, Runtimes, and their versions)
	b). Added all the jars
	c). Deployment Assembly > Java Build Path Entries.


2. Getting error of class Not found even after adding jar
	make sure you add the jar in "/ProjectNamE/src/main/webapp/WEB-INF/lib"
	and all is added in 'modulepath'
	
	
3. Comparison between Modulepath and Classpath in Eclipse's Java Build Path settings:

| Aspect                           | Modulepath													| Classpath                                            |
|----------------------------------|------------------------------------------------------------|------------------------------------------------------|
| **Purpose**                      | Manages Java modules.                                  	| Manages traditional Java projects.                    |
| **Introduced In**                | Java 9 and later.                                      	| Pre-Java 9.                                          |
| **Use in Modular Projects**      | Required for modular projects.                         	| Not applicable in modular projects.                  |
| **Configuration in Eclipse**     | Eclipse projects with module-info.java.                	| Traditional Eclipse projects without module-info.java.|
| **Contents**                     | Modules, module dependencies, and module-related settings. | JAR files, directories, and other classpath entries.  |
| **Visibility Control**           | Modules provide encapsulation, restricting access based on module declarations. | No built-in visibility control; all classes are accessible.|
| **Support for Java Modules**     | Explicitly supports Java modules using module-info.java. 	| Does not provide direct support for Java modules.    |
| **Use of Automatic Modules**     | Automatic modules are supported (JARs without module-info.java). | N/A. Automatic modules are not applicable.           |
| **Java Version Dependency**      | Requires Java 9 and later.                             	| Compatible with earlier Java versions.               |
| **Project Structure**            | Requires module-info.java file defining module structure. 	| Typically does not include module-info.java.         |

Note: The usage of Modulepath and Classpath depends on the nature of your project.
If you are working with modular projects introduced in Java 9 and later, you will use Modulepath.
For traditional projects without modules, you will use Classpath.
If you are working in a modular project, Eclipse will automatically configure the Java Build Path accordingly.