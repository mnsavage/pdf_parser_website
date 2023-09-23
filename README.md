# pdf-parser-website

## host front-end:

- Deploy the stack using command `sam deploy --guided`
- Build the front-end by going to the `pdf_parser_front_end` then running `npm run build`
- upload the files and folders in the build/ folder that was generated using `npm run build` in the website s3 bucket using aws console(Note: you must upload the files and folder individually).
- edit and disable the `Block public access(bucket settings)` in the aws console under the s3 website bucket's permission tab.
- add bucket policy under the permission tab of the website s3 bucket:
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::Bucket-Name/*"
            ]
        }
    ]
}
```
- to get the url of website you can either look at the output of the sam `deploy --guided` command or go to aws console and see it under cloudfront resource.