## Static WebApp Hosting solution on AWS with CD implementation.

1. Login into AWS console.
2. Go to CloudFormation.
    > note: we will analyse available options in CloudFormation together.
### Manual web distribution    
3. `Create stack`.
4. `Upload a template file`.
    > webapp/phase00/templates/distribution.yaml
5. `Next`.
6. Name the stack as `workshop`.
7. `Next`.
8. `Next`.
9. Tick `I acknowledge that AWS CloudFormation might create IAM resources.` && `Create stack`.
10. Wait for stack creation.
11. While cloudfront is creating, upload `webapp/phase00/index.html` to created s3 bucket.
12. Analyse `distribution.yaml` contents.
13. Visit cloudfront URL.
### Partial Continuous Deployment
14. Go to IAM and generate GIT HTTPS credentials && download the file.
15. Go to Code Commit && `Create repository`.
16. Name repository name as `workshop-website` && `create`.
17. Copy `webapp/phase01/` into new directory outside of git control i.e. `../../webapp/`.
    > cd webapp && cp -r phase01 ../../webapp
18. Change directory to new webapp folder, `Git init .` && Push `webapp/` to created repository under `develop` branch.
    ```bash
    cd ../../webapp \
    git init . \
    git remote add origin https://CODE_COMMIT_REPO
    git push origin :develop
    ```
     
19. Go to CloudFormation.
20. `Create stack`.
21. `Upload a template file`.
    > webapp/phase01/templates/ci.yaml
22. `Next`.
23. Name the stack as `workshop-ci`.
24. `Next`.
25. `Next`.
26. Tick `I acknowledge that AWS CloudFormation might create IAM resources.` && `Create stack`.
27. Analyse `ci.yaml` contents.
28. Go to Code Pipeline && Review it.
29. Run the pipeline.
30. Verify results
### Full Continuous Deployment
31. Go to cloudfront && update `workshop-ci` stack.
32. `Replace current template`.
33. `Upload a template file` `webapp/phase02/templates/distribution.yaml`.
34. Change `ProjectName` value to `workshop-next` && update stack.
35. Observe results.
### Resources clean-up
36. Delete all stacks but not `workshop-ci`.
    > why we have to first delete stacks created by CI?
37. Delete `workshop-ci`.
38. Remove all buckets from S3.