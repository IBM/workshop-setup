# Setup Jenkins on OpenShift 4.3

Pre-requirements:
- OpenShift 4.3 cluster

1. From the IBM Cloud cluster dashboard, click the `OpenShift web console` button,

    ![open OpenShift web console](../.gitbook/jenkins/openshift-web-console-button.png)

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

    ![Projects](../.gitbook/jenkins/projects.png)

6. For `Name` enter `jenkins`, for `Display Name` enter `jenkins`, and for `Description` enter `jenkins`,

    ![Create jenkins project](../.gitbook/jenkins/jenkins-project.png)

7. Click `Create`,
8. Go to `Operators` > `OperatorHub`,
9.  For `Filter by keyword` enter `Jenkins`,

    ![](../.gitbook/jenkins/operatorhub-jenkins.png)

10. Select the `Jenkins Operator` by `Community`, `provided by Red Hat`,
11. Click `Continue` to `Show Community Operator`,

    ![](../.gitbook/jenkins/show-community-operator.png)

12. Review the operator information, and click `Install`,

    ![](../.gitbook/jenkins/install-jenkins-operator.png)

13. In the `Create Operator Subscription` window, choose `A specific namespace in the cluster` and select the project `jenkins`, select `alpha` under `Update Channel`, select `Automatic` under `Approval Strategy`,

    ![](../.gitbook/jenkins/jenkins-operator-config.png)

14. Click `Subscribe`,
15. The `Installed Operators` page will load, wait until the `Jenkins Operator` has a `Status` of `Succeeded`,

    ![](../.gitbook/jenkins/installed-operator-succeeded.png)

16. Click the installed operator linked `Name` of `Jenkins Operator`,

    ![](../.gitbook/jenkins/jenkins-operator-details.png)

17. In the `Provided APIs` section, click the `Create Instance` link in the `Jenkins` panel,
18. In the `Create Jenkins` YAML definition for the new Jenkins instance, change the `metadata.name` to `my-jenkins`, accept all other specifications,

    ![](../.gitbook/jenkins/jenkins-yaml.png)

19. Click `Create`,

    ![](../.gitbook/jenkins/jenkins-instance-created.png)

20. Go to `Networking` > `Routes`, and look for a new Route `jenkins-my-jenkins`,

    ![](../.gitbook/jenkins/jenkins-route.png)

21. Click the link for `jenkins-my-jenkins` route in the `Location` column,

    ![](../.gitbook/jenkins/jenkins-route.png)

22. A route to your Jenkins instance opens in a new browser window or tab,
23. Click `Log in with OpenShift`,

    ![](../.gitbook/jenkins/login-with-openshift

24. Click `Allow selected permissions`,

    ![OpenShift Jenkins Allow selected permissions](../.gitbook/jenkins/jenkins-login-set-permissions.png)

25. Welcome to Jenkins !

    ![](../.gitbook/jenkins/welcome-to-jenkins.png)

26. Configure Jenkins
    1. Go to Jenkins > Manage Jenkins > Global Tool Configuration,
    2. Go to the `Maven` section, 
    3. Click `Maven Installations`,
    4. If no Maven installer is configured, click `Add Maven`,
    5. Configure the `Name` to be `maven`, check the option `Install automatically` and select version `3.6.3`,
    6. Click Save,

    ![OpenShift Add Maven](../.gitbook/jenkins/jenkins-add-maven.png)
