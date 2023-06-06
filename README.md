# Java Development Tools for Preparation

## Spring MVC with Database Config
* Project name : SpringWebMVC01
* JDK Runtime : 1.7.0_80
* Web Server : Apache Tomcat 8.5.0
* Database : PostgreSQL 13.11
* Library : Spring Framework, Hibernate ORM, Joda Time, servlet-api 2.5
* Dependency Management : Maven

<details>
<summary>Config web.xml</summary>
	
#### Code
```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://java.sun.com/xml/ns/javaee" xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd" id="WebApp_ID" version="2.5">
	
	<display-name>SpringWebMVC01</display-name>
	
	<context-param>
		<param-name>webAppRootKey</param-name>
		<param-value>SpringWebMVC01</param-value>
	</context-param>
	<context-param>
		<param-name>contextConfigLocation</param-name>
		<param-value>
			classpath:applicationContext.xml
		</param-value>
	</context-param>
	
	<listener>
		<listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
	</listener>
	
	<servlet>
	  <servlet-name>dispatcher</servlet-name>
	  <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
	  <init-param>
	    <param-name>contextConfigLocation</param-name>
	    <param-value>/WEB-INF/dispatcher-servlet.xml</param-value>
	  </init-param>
	  <load-on-startup>1</load-on-startup>
	</servlet>
	
	<listener>
	  <listener-class>
	  		org.springframework.web.context.request.RequestContextListener
	  	</listener-class>
	</listener>
	
	<servlet-mapping>
	  <servlet-name>dispatcher</servlet-name>
	  <url-pattern>/</url-pattern>
	</servlet-mapping>
	
</web-app>
```
</details>

<details>
<summary>Config pom.xml</summary>
	
#### Code
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	
	<modelVersion>4.0.0</modelVersion>
	
	<groupId>SpringWebMVC01</groupId>
	<artifactId>SpringWebMVC01</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<packaging>war</packaging>
	
	<name>Spring Web MVC</name>
	<description>Simple Spring MVC with Database</description>
	
	<build>
	  <sourceDirectory>src</sourceDirectory>
	  <plugins>
	    <plugin>
	      <artifactId>maven-compiler-plugin</artifactId>
	      <version>3.8.1</version>
	      <configuration>
	        <source>1.7</source>
	        <target>1.7</target>
	      </configuration>
	    </plugin>
	    <plugin>
	      <artifactId>maven-war-plugin</artifactId>
	      <version>3.2.3</version>
	      <configuration>
	        <warSourceDirectory>WebContent</warSourceDirectory>
	      </configuration>
	    </plugin>
	  </plugins>
	</build>
	
	<dependencies>
		<!-- junit 5, unit test -->
        <dependency>
            <groupId>org.junit.jupiter</groupId>
            <artifactId>junit-jupiter-engine</artifactId>
            <version>5.3.1</version>
            <scope>test</scope>
        </dependency>
        
	  	<!-- Javax Servlet -->
	  	<dependency>
	  		<groupId>javax.servlet</groupId>
	  		<artifactId>servlet-api</artifactId>
	  		<version>2.5</version>
	  	</dependency>
	  	<dependency>
	  		<groupId>javax</groupId>
	  		<artifactId>javaee-web-api</artifactId>
	  		<version>7.0</version>
	  	</dependency>
	  	
	  	<!-- Spring framework -->
	  	<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-core</artifactId>
			<version>${org.springframework-version}</version>
			<exclusions>
	  			<exclusion>
	  				<groupId>commons-logging</groupId>
	  				<artifactId>commons-logging</artifactId>
	  			</exclusion>
	  		</exclusions>
		</dependency>
		
		<dependency>
			<groupId>org.springframework.data</groupId>
			<artifactId>spring-data-jpa</artifactId>
			<version>1.3.0.RELEASE</version>
		</dependency>
		
	  	<dependency>
	  		<groupId>org.springframework</groupId>
	  		<artifactId>spring-orm</artifactId>
	  		<version>${org.springframework-version}</version>
	  	</dependency>
	  	
	  	<dependency>
	  		<groupId>org.springframework</groupId>
	  		<artifactId>spring-aop</artifactId>
	  		<version>${org.springframework-version}</version>
	  	</dependency>
	  	
	  	<dependency>
	  		<groupId>org.springframework</groupId>
	  		<artifactId>spring-context</artifactId>
	  		<version>${org.springframework-version}</version>
	  	</dependency>
	  	
	  	<dependency>
	  		<groupId>org.springframework</groupId>
	  		<artifactId>spring-context-support</artifactId>
	  		<version>${org.springframework-version}</version>
	  	</dependency>
	  	
	  	<dependency>
	  		<groupId>org.springframework</groupId>
	  		<artifactId>spring-beans</artifactId>
	  		<version>${org.springframework-version}</version>
	  	</dependency>
	  	
	  	<dependency>
	  		<groupId>org.springframework</groupId>
	  		<artifactId>spring-web</artifactId>
	  		<version>${org.springframework-version}</version>
	  	</dependency>
	  	
	  	<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-webmvc</artifactId>
			<version>${org.springframework-version}</version>
		</dependency>
	  	
	  	<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-tx</artifactId>
			<version>${org.springframework-version}</version>
		</dependency>
	  	
	  	<!-- Taglib -->
	  	<dependency>
	  		<groupId>jstl</groupId>
	  		<artifactId>jstl</artifactId>
	  		<version>1.2</version>
	  	</dependency>
	  	
	  	<!-- Hibernate framework -->
	  	<dependency>
			<groupId>org.hibernate</groupId>
			<artifactId>hibernate-core</artifactId>
			<version>${org.hibernate-version}</version>
			<!-- exclude logging at hibernate-core -->
			<exclusions>
				<exclusion>
	  				<groupId>org.jboss.logging</groupId>
	  				<artifactId>jboss-logging</artifactId>
	  			</exclusion>
			</exclusions>
		</dependency>
		
	  	<dependency>
			<groupId>org.hibernate</groupId>
			<artifactId>hibernate-entitymanager</artifactId>
			<version>${org.hibernate-version}</version>
		</dependency>
		
	  	<dependency>
			<groupId>org.hibernate</groupId>
			<artifactId>hibernate-validator</artifactId>
			<version>5.0.1.Final</version>
			<!-- exclude logging at hibernate-validator -->
			<exclusions>
				<exclusion>
	  				<groupId>org.jboss.logging</groupId>
	  				<artifactId>jboss-logging</artifactId>
	  			</exclusion>
			</exclusions>
		</dependency>
	  	
	  	<!-- Hibernate dependency -->
	  	<dependency>
			<groupId>commons-codec</groupId>
			<artifactId>commons-codec</artifactId>
			<version>1.9</version>
		</dependency>
		
	  	<dependency>
	  		<groupId>commons-dbcp</groupId>
	  		<artifactId>commons-dbcp</artifactId>
	  		<version>1.4</version>
	  	</dependency>
	  	
	  	<dependency>
	  		<groupId>commons-fileupload</groupId>
	  		<artifactId>commons-fileupload</artifactId>
	  		<version>1.2.1</version>
	  	</dependency>
	  	
	  	<dependency>
			<groupId>commons-io</groupId>
			<artifactId>commons-io</artifactId>
			<version>2.4</version>
		</dependency>
		
		<dependency>
			<groupId>commons-lang</groupId>
			<artifactId>commons-lang</artifactId>
			<version>2.6</version>
		</dependency>
		
	  	<dependency>
			<groupId>commons-logging</groupId>
			<artifactId>commons-logging</artifactId>
			<version>1.2</version>
		</dependency>
	  	
	  	 <dependency>
			<groupId>org.slf4j</groupId>
			<artifactId>log4j-over-slf4j</artifactId>
			<version>${org.slf4j-version}</version>
			<scope>compile</scope>
		</dependency>
	  	
	  	<!-- Validation -->
	  	<dependency>
	  		<groupId>javax.validation</groupId>
	  		<artifactId>validation-api</artifactId>
	  		<version>1.1.0.Final</version>
	  	</dependency>
	  	
	  	<!-- Encryptable Properties -->
	  	<dependency>
	  		<groupId>org.jasypt</groupId>
	  		<artifactId>jasypt</artifactId>
	  		<version>1.6</version>
	  		<exclusions>
	  			<exclusion>
	  				<groupId>commons-codec</groupId>
	  				<artifactId>commons-codec</artifactId>
	  			</exclusion>
	  			<exclusion>
	  				<groupId>commons-lang</groupId>
	  				<artifactId>commons-lang</artifactId>
	  			</exclusion>
	  		</exclusions>
	  	</dependency>
	  	
	  	<!-- joda-time -->
	  	<dependency>
	  		<groupId>joda-time</groupId>
	  		<artifactId>joda-time</artifactId>
	  		<version>2.4</version>
	  	</dependency>
	  	<dependency>
		    <groupId>org.jadira.usertype</groupId>
		    <artifactId>usertype.core</artifactId>
		    <version>3.0.0.CR1</version>
		</dependency>
		
		<!-- Postgresql Database Driver -->
	  	<dependency>
	  		<groupId>org.postgresql</groupId>
	  		<artifactId>postgresql</artifactId>
	  		<version>9.4-1203-jdbc4</version>
	  	</dependency>

	</dependencies>
	
	<properties>
		<org.springframework-version>3.2.3.RELEASE</org.springframework-version>
		<java-version>1.7</java-version>
		<org.slf4j-version>1.7.5</org.slf4j-version>
		<org.sitemesh-version>3.0.0</org.sitemesh-version>
		<org.codehaus.jackson-version>1.9.12</org.codehaus.jackson-version>
		<org.hibernate-version>4.1.4.Final</org.hibernate-version>
  	</properties>
  	
</project>
```
</details>

#### Config dispatcher-servlet.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:p="http://www.springframework.org/schema/p"
       xmlns:context="http://www.springframework.org/schema/context"
       xmlns:mvc="http://www.springframework.org/schema/mvc"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-3.2.xsd
        http://www.springframework.org/schema/mvc http://www.springframework.org/schema/mvc/spring-mvc-3.2.xsd
        http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context-3.2.xsd">
        
	<context:component-scan base-package="id.ac.campus.spring.controller" />
	
	<mvc:annotation-driven />
	
	<mvc:view-controller path="/" view-name="login" />
	
	<mvc:interceptors>
		<!-- Changes the locale when a 'locale' request parameter is sent; e.g. /?locale=de -->
		<bean class="org.springframework.web.servlet.i18n.LocaleChangeInterceptor" />
	</mvc:interceptors>
	
	<!-- 86400 604800 -->
	<mvc:resources mapping="/resources/**" location="/resources/" cache-period="604800"/>
	
	<bean id="localeResolver" class="org.springframework.web.servlet.i18n.CookieLocaleResolver" />
	
	<!-- 1024 MB = 1073741824 Bytes -->
	<!-- 
    <bean id="multipartResolver" class="org.springframework.web.multipart.commons.CommonsMultipartResolver">
    	<property name="maxUploadSize" value="1073741824"/>
    </bean>
     -->
    
	<bean id="jspViewResolver"
          class="org.springframework.web.servlet.view.InternalResourceViewResolver"
          p:prefix="/WEB-INF/jsp/"
          p:suffix=".jsp"/>

</beans>
```

#### Config applicationContext.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:p="http://www.springframework.org/schema/p"
       xmlns:aop="http://www.springframework.org/schema/aop"
       xmlns:context="http://www.springframework.org/schema/context"
       xmlns:jee="http://www.springframework.org/schema/jee"
       xmlns:tx="http://www.springframework.org/schema/tx"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-3.2.xsd
        http://www.springframework.org/schema/aop http://www.springframework.org/schema/aop/spring-aop-3.2.xsd
        http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context-3.2.xsd
        http://www.springframework.org/schema/jee http://www.springframework.org/schema/jee/spring-jee-3.2.xsd
        http://www.springframework.org/schema/tx http://www.springframework.org/schema/tx/spring-tx-3.2.xsd">
    
    <context:annotation-config/>
    
    <tx:annotation-driven/>

    <context:component-scan base-package="id.ac.campus.spring"/>
    
    <context:property-placeholder location="classpath:configuration.properties" />
	
	<!-- Local-DB BEGIN -->
    <bean id="dataSource" class="org.apache.commons.dbcp.BasicDataSource" destroy-method="close"
        p:driverClassName="${jdbc.driverClassName}"
        p:url="${jdbc.url}"
        p:username="${jdbc.username}"
        p:password="${jdbc.password}"
        p:initialSize="2"
        p:maxActive="50"
        p:maxIdle="15"
        p:minIdle="3"
        p:maxWait="30000"
        p:removeAbandoned="true"
        p:removeAbandonedTimeout="30"
        p:validationQuery="SELECT 1"/>
        
    <bean id="sessionFactory" class="org.springframework.orm.hibernate4.LocalSessionFactoryBean"
        p:dataSource-ref="dataSource"
        p:configLocation="classpath:hibernate.cfg.xml">
        <property name="hibernateProperties">
            <props>
            	<prop key="hibernate.cache.use_second_level_cache">true</prop>
            	<prop key="hibernate.cache.provider_class">org.hibernate.cache.EhCacheProvider</prop>
            	<prop key="hibernate.jdbc.batch_size">15</prop>
            	<prop key="hibernate.jdbc.fetch_size">1000</prop>
            	<prop key="hibernate.max_fetch_depth">30</prop>
            	<prop key="hibernate.order_inserts">true</prop>
            	<prop key="hibernate.order_updates">true</prop>
            </props>
        </property>
    </bean>

	<bean class="org.springframework.dao.annotation.PersistenceExceptionTranslationPostProcessor"/>
	
    <bean id="transactionManager" class="org.springframework.orm.hibernate4.HibernateTransactionManager">
        <!-- p:sessionFactory-ref="sessionFactory"> -->
        <property name = "sessionFactory" ref = "sessionFactory" />
    </bean>
    <!-- Local-DB END -->
    
</beans>
```

#### Config hibernate.cfg.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE hibernate-configuration PUBLIC
"-//Hibernate/Hibernate Configuration DTD 3.0//EN"
"http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">
<hibernate-configuration>
	<session-factory>
		<property name="dialect">org.hibernate.dialect.PostgreSQLDialect</property>

		<!-- remove on production -->
		<property name="show_sql">true</property>
		<property name="format_sql">false</property>
		
		<!-- Entity Mapping -->
		<mapping class="id.ac.campus.spring.entity.TblActivityLog" />
		
	</session-factory>
</hibernate-configuration>
```

#### Config configuration.properties
```xml
# Application
app.url = http://localhost:8080/SpringWebMVC01/

# PostgreSQL Driver Setup
jdbc.driverClassName    = org.postgresql.Driver
jdbc.url                = jdbc:postgresql://localhost:5432/yourdatabasename
jdbc.username           = postgres
jdbc.password 		= yourpassword
```
