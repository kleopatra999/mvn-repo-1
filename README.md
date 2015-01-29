# mvn-repo
Youtube's maven repository

### Deploying a Project

1. Clone this repository
2. Add the following section to the project's pom.xml

  ```
    <distributionManagement>
      <repository>
        <id>repo</id>
        <url>https://github.com/youtube/mvn-repo/raw/master/releases</url>
      </repository>
      <snapshotRepository>
        <id>snapshot-repo</id>
        <url>https://github.com/youtube/mvn-repo/raw/master/snapshots</url>
      </snapshotRepository>
    </distributionManagement>
  ```
3. mvn deploy to the repo's local clone and push the artifacts to Github

  ```
    mvn -DaltDeploymentRepository=snapshot-repo::default::file:/path/to/clone/of/mvn-repo/snapshots clean deploy
    cd /path/to/clone/of/mvn-repo
    git add .
    git commit -m "commit message"
    git push origin master
  ```

### Add Dependency

To add a project hosted on this repo as a dependency, add the following to your project's pom.xml

  ```
    <repositories>
      <repository>
          <id>youtube-snapshots</id>
          <url>https://github.com/youtube/mvn-repo/raw/master/snapshots</url>
      </repository>
    </repositories>
  ```
