# amazon-lookout

Step 1 - Setup S3 bucket

Enable versioning on the bucket - go to Properties -> Bucket Versioning -> Edit -> Enable and choose 'Save Changes'. This is important for verification of results later. c. Under the S3 bucket - create a train and test folder.

d. Under the train folder - create 2 folder's "normal" and "anomaly"

e. Under the test folder -- create 2 folder's "normal" and "anomaly"

e. Under the root folder -- create folder "extra_images"

----

Step 2 - Copy circuitboard dataset to S3
git clone https://github.com/aws-samples/amazon-lookout-for-vision.git
cd amazon-lookout-for-vision

    aws s3 cp circuitboard/train s3://<YOUR NEWLY CREATED S3 BUCKET NAME>/train --recursive

    aws s3 cp circuitboard/test s3://<YOUR NEWLY CREATED S3 BUCKET NAME>/test --recursive
    
    aws s3 cp circuitboard/extra_images s3://<YOUR NEWLY CREATED S3 BUCKET NAME>/extra_images --recursive

For example: S3 BUCKET NAME is lfv-amitgt-us-east-2

    aws s3 cp circuitboard/train s3://lfv-amitgt-us-east-2/train --recursive

    aws s3 cp circuitboard/test s3://lfv-amitgt-us-east-2/test --recursive

    aws s3 cp circuitboard/extra_images s3://lfv-amitgt-us-east-2/extra_images --recursive

----

Step 3 - Create a project and dataset
Go to https://console.aws.amazon.com/  and search for "Lookout For Vision" service
Click OK if you see the following screen to store your projects in a default s3 bucket.

After creating the project, click on "Create Dataset".

After clicking on "Create Dataset" you will see the following screen. Pick the training and test dataset option.

Here we are sourcing the dataset from S3 and select the training folder


----
Step 4 - Model Training and Performance Metrics
Click on the "Train Model" button

You will see the model "training in progress" and once the training completes you will see the following screen with status changed to "Training complete" - it may take about 40 minutes.
Click on "Model 1" and take a moment to review the performance results. 

----

Step 5 - Model Evaluation and Feedback

In order to evaluate the model on the new "unseen images", click on the "Trial Detections" tab under the "lookoutforvision-demo" project. From the "extra_images" folder in your Amazon S3 bucket, download any 5 images into a local folder called amazon-lookout-for-vision, on your current machine.
Click on Run trial detection and you will see the following screen. Fill the fields according to the following screen and source the trial images from your local machine.
Choose button 'Detect anomalies'. You will see the following screen with a message on the top of the screen "Trial trial001 is detecting anomalies"

----

Step 6 (Optional) - Model Retraining
Click on "Dataset" under "lookoutforvision-demo" on the left hand side of the console. You will now see 45 (40+5) images in the training dataset.

---

Step 7 - Model Deployment and Use
Click on Models tab, and click on Model 1. If you executed Step 6 you will see Model 2 as well.






