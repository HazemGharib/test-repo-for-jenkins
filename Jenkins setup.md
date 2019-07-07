# Prepare a production ready instance

## Deploy Jenkins in Docker

### 1. Pull jenkins

* `docker pull jenkins/jenkins`

### 2. Create container

* `docker container create jenkins/jenkins`

### 3. Run container with Jenkins wizard up

* `docker run -d -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins`
* **For passing env params consider using something like this :** `docker run -d -p 8080:8080 -p 50000:50000 -v --env JAVA_OPTS=-Dhudson.footerURL=http://mycompany.com jenkins_home:/var/jenkins_home jenkins/jenkins`

### 4. Open new terminal and execute bash to have access into the newly run container

* `docker exec -it <container_id> bash`
* **You can get *container_id* by this command** : `docker container ls`

### 5. Go to `/var/jenkins_home/secrets/initialAdminPassword` to get initial password

### 6. Browse localhost:8080 and enter the obtained password

### 7. Choose what plugins to install, use the recommended option to install the mostly used plugins

### 8. Enter your own config for admin user

### 9. Enter the Jenkins URL you want

### 10. Close the running instance of the container after completing everything and then restart it again

### 11. Hit the URL that you specified for Jenkins and enter your credentials

* * *

#### Help page

* For more details on Jenkins docker installation click [here](https://github.com/jenkinsci/docker/blob/master/README.md)

* * *

## Prepare a Multibranch pipeline

### 1. Hit the Jenkins URL

### 2. Create a *New Item* from the menu at the left

### 3. Choose *Multibranch Pipline* and enter an item name and hit ok

### 4. In the *General* tab enter a display name and an optional description

### 5. In the *Branch Sources* tab add a new *Git* source, Enter the project repository and add it's own credintials, Select *Discover branches* from *Behaviors*, Select *Named branches get different properties* from *Property strategy*

### 6. In the *Scan Multibranch Pipeline Triggers* tab check the option *Periodically if not otherwise run* and specify an *Interval*

### 7. In the *Orphaned Item Strategy* tab check the *Discard old items* option and specify the number of *Days to keep old items* and the *Max # of old items to keep*

### 7. Hit *Save* to save the pipeline changes
