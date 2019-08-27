# 07 API GATEWAY BASICS.

Amazon API Gateway is a fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale. 

## LAB

1. Go Go to **API GATEWAY** web console.
2. Select available API.
3. Review the options.
4. Go to **API Keys**.
5. **Actions -> Create API key**.
6. Name it as **myKey** && **Save**.
7. Go to **Usage Plans** && **Create**.
8. Name it as **myUsagePlan**.
9. Untick checkboxes && **Next**.
10. **Add API Stage**.
11. Select available API and Stage && **Next**.
12. **Add API Key to Usage Plan**.
13. Type **myKey** && Submit.
14. Deploy resources to default stage (**Resources- > Actions -> Deploy API -> Default-> Deploy**)
10. Test again api endpoint, for example https://vfm4vyn7sj.execute-api.eu-west-1.amazonaws.com/default/myBackend?TableName=storage.
11. Add **x-api-key** header equal to **api key** value to your request and test it with CURL or in Postman. For example: `curl https://vfm4vyn7sj.execute-api.eu-west-1.amazonaws.com/default/myBackend?TableName=storage --header "X-Api-Key:API_KEY"`.
12. Remove Lambda Function.
13. Remove DynamoDB table.
14. Delete **myBackendRole** from IAM roles.
15. Remove API Gateway.