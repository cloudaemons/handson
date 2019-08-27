# 04. DYNAMODB IN MINUTES

## DYNAMODB

Amazon DynamoDB is a key-value and document database that delivers single-digit millisecond performance at any scale.

## LAB

1. Go to the  **DynamoDB** web console.
2. **Create table**.
3. Name: **storage**, Primary key: **id**.
4. Untick **Use default settings**.
5. Choose **On-demand** read/write capacity mode
6. Click **Create**.
7. When table created go to **Items** tab.
8. Click **Create item**.
9. Add single item with id equal to **test**.
10. Open in the browser API Endpoint from Lambda labs with additional query parameter **TableName=storage**. For example https://vfm4vyn7sj.execute-api.eu-west-1.amazonaws.com/default/myBackend?TableName=storage.
11. Do not delete resources.