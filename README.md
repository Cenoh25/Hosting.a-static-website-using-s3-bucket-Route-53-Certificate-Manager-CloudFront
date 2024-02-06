# Hosting a-Static-Website-in AWS-using-S3 bucket-Route53-Certificate Manager-CloudFront

In this project I created a static website in AWS using S3 bucket, Route 53, Certificate Manager and CloudFront.
Scenario: Lets imagine you have a company with a marketing department, and you have to decide on how to launch a new promotional campaign on a static website. This website has to showcase your latest products and offers. 
In order to ensure high availability and optimal performance, I can choose to host the website on AWS.
I will create an s3 bucket to store content. This will ensure scalability and cost effectiveness.
Route 53 will be used for domain management. This will enable users/customers to access the website via a user friendly domain name.
The certificate manager will help secure the website with SSL certificate. This will ensure that the website is accessible through Https instead of Http.
Cloudfront will serve as a content delivery network (CDN). This will accelerate content delivery to users worldwide ensuring faster load time and a seamless browsing experience.

When customers access the website it will result to an end point from route 53. The end point will be redirected to amazon cloudfront to help serve the customers as well as help to reduce the latency and give a better user experience to the customers. The website will be created using the HTTPS protocole. This will make it more secure and this will be done using the certificate manager. Finally cloudfront will reach out to the S3 bucket to serve the users/customers with the contents of the website. 

Story 1: I created a domain name (cenoh.com). One can be purchased either on the amazon console or on go daddy. I created an S3 bucket and I made accessible to the public. Content was added to the s3 bucket but uploading flies. Once files were added to the bucket, I created a bucket policy to give permission for these files to be accessed globally. 

Story 2: Once the bucket was created, I had to enable the static website. Inorder to do this, I "enabled" it, and I specified the index document "Index.html" and then I saved changes.

Now the we have the domain name, s3 bucket with necessary permissions. The website has been created with its content.

Story 3: Route 53 will be needed for domain management and registration. I created a hosted zone. A hosted zone is a container for records. In a nut shell it tells route 53 how to respond to DNS queries for a domain.

So far I have created a domain name, s3 bucket and hosted zone in route 53. Next, I will need to create the certficate manager.

Story 4: We need to request for a certificate because we need the SSL certificate to make our website secure. We need to request for a certificate,we need to add our domain name and click on request. To view our certificate, we need to click on "view" and wait for it to valide (no longer in pending mode) 

Story 5: I now need to create a record set in route 53. In order to do this, I need to go to the hosted zone I created and create record. The type of record that I will be creating is a CNAME record. I am using CNAME record because it will help map the domain name to amazon S3 bucket. By doing this I can access our s3 bucket using my own domain name (instead of using the long URL from the s3 bucket). I also need to add a sub domain name. In order to do this I need to go back to the certificate manager and copy the CNAME name and CNAME value (must be copied without the domain name). Once the CNAME name and CNAME value have been copied both have to be pasted under record name (CNAME name) and value (CNAME value) and click create records. 

Story 6: Finally to create CloudFront distribution, I copied the URL from the s3 bucket under static website hosting and pasted it in cloud front (remove http//). I then redirected http to https because I now have the SSL certificate through the certificate manager. I then added an alternate domain name (I added my own domain name). I then added my custom SSL certificate and I created the cloudfront distribution and wait for it to finish deploying.

Once it deployed successfully, I copied the distribution domain name and pasted it in a browser to make sure that it is working. 

Story 7: Once the distribution domain name has been verified, I needed to make sure that I could access the website using my own domain name. In order to do this I created a record set in route 53. I chose record type A and toggled alias to see the different options available. I then routed my traffic to cloud front distribution and I created the record. Once the record is "insync", I then verified the domain name to make sure that it could be securely accessed through a browser using https. 


The website has now been created and hosted in Amazon S3 and it can be accessed over https. Users/customers will access the URL which will result from an end point through route 53. The end point will be redirected to amazon cloud front to serve our global audience which will help to reduce latency and give a better user experience to the customers. And because I issued a certificate using the certificate manager, I am able to use SSL and access the website through https instead of http. Finally, cloudfront will reachout to amazon s3 bucket to serve the customers/users with the content. 


