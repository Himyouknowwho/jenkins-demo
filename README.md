# jenkins-demo
Demo setup for: Level Up Your Development Workflow with Jenkins!


To start:
```
docker compose up -d
```


When starting Jenkins for the first time, it will ask for a initial password.
You can use this command to extract it:

```
docker exec jenkins-blueocean-demo cat /var/jenkins_home/secrets/initialAdminPassword
```
And paste it in to the textfield in the browser.