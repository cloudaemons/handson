# 03. QUICK SETUP OF NODE SERVER

## ELASTIC BEANSTALK

Elastic Beanstalk is an orchestration service offered by Amazon Web Services for deploying applications which orchestrates various AWS services, including EC2, S3, Simple Notification Service (SNS), CloudWatch, autoscaling, and Elastic Load Balancers

## LAB

1. Go to the  **Elastic Beanstalk** web console.
2. Click create new application **node-server**
2. Name your application as **node-server**
3. Click **Create**
4. Go to actions and choose **Create environemnt**
5. Choose **Web server environment**
6. Select **Node.js** as a platform.
7. Click on **Configure more options**
8. Review possible options.
9. Change ennvironment type to **Load balanced**
10. Change Capacity to scale up to 2 instances 
11. Review Load Balancer.
12. Click **Create environemnt**
10. When Elastic Beanstalk ready go to **Dashboard** && click on its URL in the header (for example: nodeserver-env.3heynkzhuy.eu-west-1.elasticbeanstalk.com).
11. Select **Actions -> Terminate Environment**.