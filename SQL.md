# Quereis
Change/alter the table (enum list)

Hibernate: alter table user modify column user_type enum ('GUEST','AdminUser','NormalUser') not null


# Errors solving
>> If error occur like: - Table 'DBName.tableName' doesn't exist

	<property name = "dialect">org.hibernate.dialect.MySQL5Dialect</property>	
			w							OR
	<property name = "dialect">org.hibernate.dialect.MySQL8Dialect</property>	
	
------------------------------------------------------------------------------------------------------------------


>> 	Getting server jakarka realated error of not present:
	Check the project properties > project facets > runtimes
				and
	Check all the added libs and jars are checked in order and module


-------------------
>> 	java.lang.ClassNotFoundException: com.mysql.cj.jdbc.Driver
	at org.apache.catalina.loader.WebappClassLoaderBase.loadClass(WebappClassLoaderBase.java:1437)
	at org.apache.catalina.loader.WebappClassLoaderBase.loadCla
	
------------------------------------------------------------------------------------------------------------------
 	Add Jar in buildpath > classpath
				and 
	Add jar in server > open launch config > classpath > user entities