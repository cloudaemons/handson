### 08 Basic Single Page App hosting on AWS with Code Pipeline support.

The goal of this exercise is to learn how to host static webapp on S3 as well as put CD solution in place. 

1. Clone this repository to your local file system.

   `Make sure, you are always in eu-west-2 (Ireland) region`
2. Go to S3 (https://s3.console.aws.amazon.com/s3/home?region=eu-west-1#)
3. Create a bucket 
4. webapp-konstancin-`your_acronym` for example `webapp-konstancin-pzm`
5. Next
6. Next
6. Untick `Block all public access`
7. Next && Create bucket
8. Navigate to your bucket
9. Go to Properties && Static website hosting
10. `Use this bucket to host a website` 
11. Fill `Index document` with `index.html`.
12. `Save`.
    > note `Endpoint`
13. Go to Permissions && Bucket Policy
14. Paste and make sure in the below snippet your bucket name is correct:
    ```bas
    {
      "Version":"2012-10-17",
      "Statement":[{
        "Sid":"PublicReadGetObject",
            "Effect":"Allow",
          "Principal": "*",
          "Action":["s3:GetObject"],
          "Resource":["arn:aws:s3:::webapp-konstancin-pzm/*"
          ]
        }
      ]
    }
    ```
15. Click `Save`
16. Go to CodeCommit (https://eu-west-1.console.aws.amazon.com/codesuite/codecommit/repositories?region=eu-west-1)
17. Create Repository
18. Name Repository `webapp`
19. Click `Create`
    > note clone command
20. Go to IAM (https://console.aws.amazon.com/iam/home?region=eu-west-1)
21. Go to Users
22. Open Security Credentials.
23. Scroll down to `HTTPS Git credentials for AWS CodeCommit`.
24. Press generate and store the file.

    `training-user-at-XXXXXXX`
    `ODh4x0XymRuPEjaL7Y3ESHLy1koBaUZUEcaN1yyIezU=`
    
25. `cd 08.\ SINGLE\ PAGE\ APP\ HOSTING/ && cp -r . ../../webapp`
26. Verify new webapp folder is created.

27. 
    ```bash
    git init . &&
    git add . &&
    git commit -m 'init' &&
    git remote add origin https://git-codecommit.eu-west-1.amazonaws.com/v1/repos/webapp &&
    git push origin develop
    ```

28. Provide user and password taken from IAM.
29. Go to code commit and verify code.
30. Go to CodePipeline (https://eu-west-1.console.aws.amazon.com/codesuite/codepipeline/pipeline/new)
31. `Create Pipeline`.
32. Name the pipeline `spa-ci`.
33. Choose `New service role` with `Role name` `codepipelineServiceRole`.
34. Next.
35. Select AWS Code Commit as source provider.
36. `webapp` as repository.
37. `develop` as a branch name.
38. Next.
39. Build provider `AWS CodeBuild`.
40. Create project with name `webapp`.
41. `Operating system`: `Amazon Linux 2`.
42. Runtime `Standard`.
43. `Always use the latest image for this runtime version`.
44. Image `aws/codebuild/...`
45. `Continue to CodePipeline`.
45. `Next`.
47. `Skip deploy stage` && `skip`.
48. `Create pipeline`
49. Go to CodeBuild and modify project. (https://eu-west-1.console.aws.amazon.com/codesuite/codebuild/projects/webapp/edit/environment?region=eu-west-1)
50. `Additional configuration`.
51. Add `MICROSITE_S3_BUCKET` Environment Variable with the name of your S3 bucket i.e. webapp-konstancin-`your_acronym`.
52. Note your Service Role `codebuild-webapp-service-role`
53. `Update environment`.
54. Review CodePipeline.
55. Review CodeBuild details.
56. Open IAM.
57. Roles.
58. Find `codebuild-webapp-service-role`.
59. Permissions.
60. Click on policy called `CodeBuildBasePolicy-webapp-eu-west-1`.
61. Edit policy.
62. JSON.
63. Edit attached policy and after last statement add
    ```bash
    ,
            {
                "Effect": "Allow",
                "Resource": [
                    "arn:aws:s3:::webapp-konstancin-pzm*"
                ],
                "Action": [
                    "*"
                ]
            }
    ```
    
64. Click `Review policy` && `Save changes`.
65. Go to code pipeline.
66. Run manually the pipeline with `Release change`..
67. Navigate in the browser to s3 endpoint.
68. Delete code commit, code pipeline, s3 buckets, roles, code build.