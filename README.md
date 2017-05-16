This repo is to reproduce a strange behaviour in displaying Maven relase plugin tags.

To reproduce:
1. create a simple maven project, i.e. form the webapp maven archetype
1. add some commits, and update the pom.xml so that it contains these information:  
	```
	<scm>
	  <connection>scm:git:git@git</connection>
	  <tag>HEAD</tag>
	</scm>
	```  
	and:
	```
	<build>
      ...
      <plugins>
      ...
        <plugin>
          <groupId>org.apache.maven.plugins</groupId>
          <artifactId>maven-release-plugin</artifactId>
          <version>2.5.3</version>
        </plugin>
        ...
      </plugins>
      ...
    </build>
	```
1. run `mvn release:prepare -DpushChanges=false -DlocalCheckout=true -DreleaseVersion=1.0.0 -DdevelopmentVersion=1.0.1-SNAPSHOT` with the version numbers you prefer
1. add some more commits

The result should look something like this:

![](images/sourcetree_1.8.2.11.jpg?raw=true)
