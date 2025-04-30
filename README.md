# Hybrid-Cryptography
Hybrid cryptography combines symmetric and asymmetric encryption. Asymmetric encryption securely shares the symmetric key. The symmetric key is then used for fast and secure data encryption.

1. Cloud Computing Implementation
To effectively demonstrate the practical application of hybrid cryptography in cloud environments, we will implement a hybrid cryptographic system using various AWS services. This implementation focuses on leveraging the capabilities of AWS Lambda, API Gateway, and DynamoDB to create a secure and scalable solution.

1.1 Introduction to AWS Cloud Services
Amazon Web Services (AWS) offers a suite of cloud computing services that enable scalable, flexible, and cost-effective solutions. For this project, AWS Lambda, AWS API Gateway, and Amazon DynamoDB were utilized to implement and manage the hybrid cryptography system in the cloud.

1.2 AWS EC2 Instance
Amazon Elastic Compute Cloud (Amazon EC2) is a web service that offers a configurable compute capacity in the cloud that allows users to launch virtual servers, known as instances, to run applications on the Amazon Web Services (AWS) infrastructure. Amazon EC2 eliminates the need for investing in hardware upfront, providing scalable and flexible computing resources that can be tailored to specific requirements.To ensure accurate and consistent performance measurements of our cryptographic algorithms, we utilized an Amazon EC2 instance to run our encryption and decryption code. By conducting our tests on a standardized cloud environment, we can obtain reliable data on encryption time, decryption time, and throughput, which may vary significantly when run on high-specification personal laptops or diverse user systems worldwide.
        1.2.1 Why AWS EC2 over AWS Lambda for Performance Analysis
                    While AWS Lambda provides a serverless architecture that can simplify deployment and scalability, using it for performance analysis of         
               cryptographic algorithms might introduce variability due to its nature. Lambda functions have cold start times, which can affect the consistency of                    performance measurements. For precise performance analysis, EC2 instances are preferable due to their consistent and dedicated resources, which 
                  ensure repeatable and reliable measurements.

1.3 AWS Lambda
AWS Lambda is a serverless computing service that enables you to run code without provisioning or managing servers. AWS Lambda can scale the program by running the
code by responding to each trigger. The architecture of AWS Lambda utilized is attached as fig 1.1.

1.4 Why use AWS Lambda over EC2 (Elastic Cloud Computing) instance
    ---> No Idle Costs
              There are no charges when your code is not running, eliminating costs associated with idle instances. Whereas, AWS EC2 costs charges even during the                period of low activity or inactivity unless lowest specifications are selected for the instance.
    --->Automatic Scaling
              Lambda can scale any program by running the code in response to each trigger, handling thousands of requests per second without any manual       
              intervention.

1.5 Implementation in Cloud
The cryptographic algorithms (AES, DES, RSA, and NIKGSR) were implemented as Lambda functions. These functions handle the encryption and decryption processes.

1.6 AWS API Gateway
AWS API Gateway is a fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale. API Gateway was used to expose the Lambda functions as HTTP (Hypertext Transfer Protocol) endpoints. This setup allows the encryption and decryption services to be accessible via API calls from any device. API Gateway handles the routing of requests to the appropriate Lambda functions, ensuring secure and efficient communication between clients and the cryptographic services. The specifications, resources and method of the API gateway are in Fig. 1.2.

1.7 AWS DynamoDB
Amazon DynamoDB is a key-value and document database that delivers single-digit millisecond performance at any scale. DynamoDB was used to store the encrypted and decrypted messages. Each message is stored with a metadata (user id or else known as customer number) facilitating efficient retrieval and auditing. The integration with Lambda allows for automatic data storage and retrieval, ensuring a smooth workflow for encryption and decryption operations. The information of the table “Messages” created in DynamoDB is in Fig. 1.3.

1.8 Postman
Postman is a powerful and user-friendly tool for testing and developing APIs, offering a comprehensive interface that allows users to construct and send HTTP requests with various methods such as GET, POST, PUT, and DELETE. It enables customization of requests through headers, query parameters, and different body formats including JSON (JavaScript Object Notation) and XML (eXtensible Markup Language). Postman provides detailed response inspection, with features like status codes, headers, and pretty-printing of JSON and XML responses. Additionally, it supports organizing requests into collections, managing different environments, and automating tests with pre- and post-request scripts. Postman also facilitates collaboration by allowing users to share collections, environments, and test scripts with team members, making it an essential tool for API development and testing.

1.9 Integration with Postman for API Testing
To validate the functionality and performance of the hybrid cryptographic system, Postman application has been used to connect to the API Gateway. Postman is a popular tool for testing APIs, allowing us to send requests, inspect responses, and ensure that our API endpoints are working as expected.
In this hybrid cryptographic system, the POST HTTP method is utilized to send data for encryption and save it in the database, ensuring secure storage and efficient processing. Users submit their data via the POST request to the `/encrypt` endpoint, where it undergoes encryption before being stored. Conversely, the GET HTTP method is employed to retrieve the decrypted information from the database. By sending a GET request to the `/decrypt` endpoint with the appropriate data ID as a query parameter, users can access their original, decrypted data. This dual-method approach allows for a seamless and secure workflow in managing encrypted data within the cloud environment.
