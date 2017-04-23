# spring-boot-docker-kubernetes-example

To build docker image:
```
mvn clean package docker:build
```
To run docker container:
```
docker run -p 8080:8080 -t djhurley/spring-boot-docker-kubernetes-example
```
To build docker image and push to docker hub:
```
mvn clean package docker:build -DpushImage
```
To be able to push image to docker hub you need to add the following to your maven settins.xml:
```
<settings>
	<servers>
		<server>
			<id>docker-hub</id>
			<username>{docker hub account docker id}</username>
			<password>{docker hub account password}</password>
			<configuration>
				<email>{your email for docker hub account}</email>
			</configuration>
		</server>
	</servers>
</settings>
```
