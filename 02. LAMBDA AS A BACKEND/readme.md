# 02. LAMBDA AS HTTP BACKEND

## AWS LAMBDA

Computing service that runs code in response to events and automatically manages the computing resources required by that code. With Lambda, you can run code for virtually any type of application or backend service - all with zero administration.

## LAB

1. Go to the  **Lambda** web console.
    > make sure you are in eu-west-1 (Ireland) region.
2. Click **Create Function**
3. Select **Use a blueprint**
4. In text input type **microservice** && select **microservice-http-endpoint** && click **Configure**.
5. Name your function as **myBackend**.
6. Name your role as **myBackendRole**.
7. Select **Create a new API**
7. Select security as **Open**
8. Click **Create function**
    > API provisioning my take a few seconds.
9. On **Configuration** tab click on **API Gateway** && note **API endpoint**`
10. Open noted endpoint in the browser.
11. Do not remove resources.

