# Troubleshoot and resolve the issue of static website s3 bucket
  - Create an s3 bucket with index.html and error.html files 
  - Make sure "Static website hosting" is enabled under properties and if it is disabled, make it enabled and specify the index and error documents then save the changes.
  - Open the link that is located under Bucket website endpoint and it returns 403 authentication/access issue
  - Head to s3 bucket permission and make sure the the bucket is public; if not, disable to block public access  and edit the "Bucket policy" and add the bucket permission policy there as follows;
   
    ```
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
                    "arn:aws:s3:::s3-static-website-troubleshoot/*"
                ]
            }
        ]
    }
    ```

- And save the changes
- Head to s3 bucket properties and click on the link provided under "Static website hosting"
- Make sure the index.html file is displayed