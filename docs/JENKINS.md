## Jenkins

Pre-requirements:
- OpenShift 4.x cluster

1. From the IBM Cloud cluster dashboard, click the `OpenShift web console` button,

    ![open OpenShift web console](images/jenkins/openshift-web-console-button.png)

2. First we need to create a new project named `jenkins` to deploy the Jenkins service to,

3.  From the terminal,

    ```
    oc new-project jenkins
    ```

    outputs,
    
    ```
    $ oc new-project jenkins
    Now using project "jenkins" on server "https://c107-e.us-south.containers.cloud.ibm.com:31608".
    ```

4. Or in the Openshift web console, go to `Home` > `Projects`,
5. Click `Create Project`

    ![Projects](images/jenkins/projects.png)

6. For `Name` enter `jenkins`, for `Display Name` enter `jenkins`, and for `Description` enter `jenkins`,

    ![Create jenkins project](images/jenkins/jenkins-project.png)

7. Click `Create`,
8. Go to `Operators` > `OperatorHub`,
9.  For `Filter by keyword` enter `Jenkins`,

    ![](images/jenkins/operatorhub-jenkins.png)

10. Select the `Jenkins Operator` `provided by Red Hat`, labeled `community`,
11. Click `Continue` to `Show Community Operator`,

    ![](images/jenkins/show-community-operator.png)

12. Review the operator information, and click `Install`,

    ![](images/jenkins/install-jenkins-operator.png)

13. In the `Install Operator` window, in the `Update Channel` section, select `alpha` under `Update Channel`, choose `A specific namespace in the cluster` and in the `Installed Namespace` section, select the project `jenkins` from the dropdown, select `Automatic` under `Approval Strategy`,

    ![](images/jenkins/jenkins-operator-config.png)

14. Click `Install`,
15. The `Installed Operators` page will load, wait until the `Jenkins Operator` has a `Status` of `Succeeded`,

    ![](images/jenkins/installed-operator-succeeded.png)

16. Click the installed operator linked `Name` of `Jenkins Operator`,

    ![](images/jenkins/jenkins-operator-details.png)

17. In the `Provided APIs` section, click the `Create Instance` link in the `Jenkins` panel,
18. In the `Create Jenkins` window, select `Form View` or `YAML View` for the new Jenkins instance, change the `metadata.name` to `my-jenkins`, accept all other specifications,

    ![](images/jenkins/jenkins-yaml.png)

19. Click `Create`,

    ![](images/jenkins/jenkins-instance-created.png)

20. Go to `Networking` > `Routes`, and look for a new Route `jenkins-my-jenkins`,

    ![](images/jenkins/jenkins-route.png)

21. Click the link for `jenkins-my-jenkins` route in the `Location` column,

    ![](images/jenkins/jenkins-route.png)

22. A route to your Jenkins instance opens in a new browser window or tab,
23. If your page loads with a `Application is not available` warning, your Jenkins instance is still being deployed and you need to wait a little longer, keep trying until the Jenkins page loads,
24. You can see the progress of the Jenkins startup, by browsing to the Pods of the Deployment of the Jenkins instance that is being created,
25. Click `Log in with OpenShift`,

    ![](images/jenkins/login-with-openshift.png)

26. Click `Allow selected permissions`,

    ![OpenShift Jenkins Allow selected permissions](images/jenkins/jenkins-login-set-permissions.png)

27. Welcome to Jenkins !

    ![](images/jenkins/welcome-to-jenkins.png)

28. Configure Jenkins
    1. Go to Jenkins > Manage Jenkins > Global Tool Configuration,
    2. Go to the `Maven` section, 
    3. Click `Maven Installations`,
    4. If no Maven installer is configured, click `Add Maven`,
    5. Configure the `Name` to be `maven`, check the option `Install automatically` and select version `3.6.3`,
    6. Click Save,

    ![OpenShift Add Maven](images/jenkins/jenkins-add-maven.png)
