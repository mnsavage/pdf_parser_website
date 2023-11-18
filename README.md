# pdf-parser-website

## website aws services architecture
![image](https://github.com/mnsavage/pdf_parser_website/assets/60998598/54f179c1-6d89-48af-9694-e8d2f7cdefbd)


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
- got to the `setting` tab of the `pdf_parser_website`
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

