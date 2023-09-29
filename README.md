# pdf-parser-website

## setup AWS CLI
- You must setup AWS CLI with your access key and secret access key to deploy aws stack([link](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html))

## basic sam AWS commands:
- `sam build`: builds the sam template.yaml file
- `sam validate`: validate the sam template.yaml file(linting and format check)
- `sam deploy --guided`: deploy AWS stack to AWS console using sam template.yaml file
- `sam delete`: delete the stack you have deploy in AWS console


## host front-end manually:

- Deploy the stack using command `sam deploy --guided`
- Build the front-end by going to the `pdf_parser_front_end` then running `npm run build`
- upload the files and folders in the build/ folder that was generated using `npm run build` in the website s3 bucket using AWS console(Note: you must upload the files and folder individually).
- to get the url of website you can either look at the output of the sam `deploy --guided` command or go to AWS console and see it under cloudfront resource.

## host front-end using github action(CI):
- go to `pdf_parser_website` repository on github
- `action tab` of repository
- on the side bar click on `Deploy to AWS` action
- click on `Run work flow` button
![image](https://github.com/mnsavage/pdf_parser_website/assets/60998598/b45c82a3-f584-49c9-8298-012ea0e47fe6)

