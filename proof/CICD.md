# What is CI/CD?
> Continuous Integration/Continuous Delivery (CI/CD) is a set of practices that help software development teams deliver code changes more frequently and reliably. [infoworld](https://www.infoworld.com/article/3271126/what-is-cicd-continuous-integration-and-continuous-delivery-explained.html)

![image](https://github.com/Arthur-Brouwers/ArthurBrouwers/assets/124791770/6f266373-c312-44c6-b458-92233333b7c2)

## Continuous Intergration
Continuous Integration (CI) is a software development practice that requires developers to integrate code into a shared repository several times a day. Each check-in is then verified by an automated build, allowing teams to detect problems early. By integrating regularly, you can detect errors quickly and locate them more easily.

### How did I inmplement Continuous Improvement in my project?
To make use of continous improvement, we created new branches for each new feature. When we finished the new feature, we can make a pull request to merge the branch into "main".

Once the pull request has been made, it will trigger our [CI pipeline](https://github.com/ArthurBrouwersSemester3/Front-end/blob/main/.github/workflows/test.yml). Our CI pipeline will build the project and install all necessary packages to see if it is able to successfully run. For the repositories that have integration- and unit tests, it will also make sure to run these tests. 
Our SonarCloud runs simultaneously. If either the tests fail or the SonarCloud fails, merging is blocked. 

Additionally, since we are working together on the project, the other one needs to add a code review and approve the merge. 

After all these steps are successful, you are able to merge into main. 

## Continuous Delivery
Continuous Delivery (CD) is an extension of Continuous Integration where automated builds are deployed to a staging or production environment. The goal of Continuous Delivery is to enable a constant flow of changes into production via automated deployments.
 
### How did I inmplement Continuous Devivery in my project?
To make use of Continuous delivery, we made use of Docker. If the merge into main was successful, our [CD pipeline](https://github.com/ArthurBrouwersSemester3/Front-end/blob/main/.github/workflows/DockerImage.yml) creates and pushes the project as a docker image to Dockerhub.

In our API, it is important that our .jar file is up to date. In that case, we integrated a rebuild in our [API CD pipeline](https://github.com/ArthurBrouwersSemester3/API/blob/main/.github/workflows/Docker-Build-Push.yml)
