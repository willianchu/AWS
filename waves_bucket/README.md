# AWS Static Site Hosting

updates data from the waves conditions once in a day

![site preview](/waves_bucket/snapshot.jpg)
http://lab-waves-bucket.s3-website-us-east-1.amazonaws.com/

follow policy access file restriction

# Instructions

You can easily host your own static site in AWS:

## Create a Bucket
1. Open AWS console
2. look for "S3 services"
3. Create bucket
    1. Bucket name
    2. AWS Region (near from your consumers region) - scrow down
    3. ACLs (enabled)
    4. Object writer (mark) - scrow down
    5. Block all public access
        1. Accept the changes (deprecated)

![accept](/waves_bucket/accept.jpg)
    6. Default Encryption (enable)
    7. Accept Amazon S3 keys (SSE-S3)
    8. CREATE BUCKET

## Upload Static Site Files
name_of_the_bucket (View Details)
1. Upload 
2. Select Files
3. Close

## Change files name *optional
1. Select file
2. action (button list)
3. edit

## Configure for host static website
    1. properties(TAB) static site (enable) 
    2. Static website hosting (edit)
    3. Enable
    4. Host a static website
    5. confirm the name of the index.html file
    6. save changes
    
## Policies
1. Permissions (TAB)
	{
	  "Id": "StaticWebPolicy",
	  "Version": "2012-10-17",
	  "Statement": [
	    {
	      "Sid": "S3GetObjectAllow",
	      "Action": [
	        "s3:GetObject"
	      ],
	      "Effect": "Allow",
	      "Resource": "arn:aws:s3:::lab-waves-bucket/*",
	      "Principal": "*"
	    }
	  ]
}

* a common error is to forgot "/*" after the name of the resource path
