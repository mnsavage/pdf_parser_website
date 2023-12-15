# pdf-parser-website

## github actions:
- In this repository, each time a pull request (PR) is submitted, a GitHub Action is activated. This Action is responsible for building the stack on AWS and then deleting it afterward. This process serves as a verification method to ensure that new changes still permit the stack to be successfully built.
- This repository features a GitHub Action workflow that can be manually triggered to automatically deploy the website by building it in AWS. It's important to note that the stack in AWS must be manually deleted after deployment when using this workflow.

## website aws services architecture:
![image](https://github.com/mnsavage/pdf_parser_website/assets/60998598/54f179c1-6d89-48af-9694-e8d2f7cdefbd)

## github repository architecture:
![image](https://github.com/mnsavage/pdf_parser_website/assets/60998598/804d2f89-7837-42d0-87e4-a2cd0ba37b50)


## documentation on tools and services used in this repo:
### sam
- use for deploying website to aws
- doc: https://docs.aws.amazon.com/serverless-application-model/
### github action
- use for automating deployment of website 
- doc: https://docs.github.com/en/actions

## setup AWS CLI
- You must setup AWS CLI with your access key and secret access key to deploy aws stack([link](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html))

## basic sam AWS commands(deploy locally):
- `sam build`: builds the sam template.yaml file
- `sam validate`: validate the sam template.yaml file(linting and format check)
- `sam deploy --guided`: deploy AWS stack to AWS console using sam template.yaml file
- `sam delete`: delete the stack you have deploy in AWS console

## set up github action secrets to deploying website with github action:
- go to the `setting` tab of the `pdf_parser_website`
- navigate to `secrets and variables` and click `Actions`
- add `AWS_ACCESS_KEY_ID` secret: can get from aws console
- add `AWS_SECRET_ACCESS_KEY` secret: can get from aws console
- add `DOCKER_HUB_ACCESS_TOKEN` secret: access token for docker hub account
- add `DOCKER_HUB_USERNAME` secret: username of docker hub account
- add `SECURITY_GROUP_ID` secret: can get from aws console in EC2 -> security group
- add `SUBNET_ID` secret: can get from aws console in VPC -> subnet

## deploy website with github action(CI/CD deploy):
- go to `pdf_parser_website` repository on github
- `action tab` of repository
- on the side bar click on `Deploy to AWS` action
- click on `Run work flow` button
![image](https://github.com/mnsavage/pdf_parser_website/assets/60998598/b45c82a3-f584-49c9-8298-012ea0e47fe6)

# Notes to next group working on this project:
- At present, the back-end experiences slowness during the execution of batch jobs for PDF validation. To address this, consider not storing the Docker image on Docker Hub, but instead using AWS ECR for storage. Once this adjustment is made, the front-end can be configured to make GET protocol requests every 5 seconds, rather than at 30-second intervals.
- Please be aware that deploying multiple stacks to AWS is not feasible with this setup, as some of the resources created in AWS do not have unique names, leading to potential conflicts.
- Testing changes that span across multiple repositories is currently challenging, as it requires building the stack each time to verify new modifications. A potential solution to streamline this process is the implementation of higher-level testing methods, such as integration tests. These can provide a more efficient way to validate the functionality of new changes without the need for frequent stack builds.

