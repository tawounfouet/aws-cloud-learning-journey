

## Default Amazon Machine Image (AMI) for Amazon EC2
Hello learners!

As of March 15, 2023 the default Amazon Machine Image (AMI) for Amazon EC2 has been updated to use the Amazon Linux 2023 AMI. In the demonstrations for this course, we use the Amazon Linux 2 AMI. If you are following along with the videos please be aware that if you use the new Amazon Linux 2023 AMI with the user data the way it appears in the videos the script will not run properly and the application will not launch. We are in the process of updating the course to reflect this change.

In the meantime, there are a few ways to work around this issue. You can either use the Amazon Linux 2 AMI with the user data as shown in the demonstrations and this will resolve the issue, or you can use an updated version of the user data script which I will include in this message.

To recap, we have a new default AMI for EC2 instances called the Amazon Linux 2023 AMI. The videos show us using Amazon Linux 2. Because of changes between these two AMIs the user data script shown in the videos will not run properly on Amazon Linux 2023 based instances. You can either choose Amazon Linux 2 as the AMI when launching the instance, and use the original user data script or you can use the Amazon Linux 2023 AMI and use the updated user data script.

Amazon Linux 2 user data script:

          #!/bin/bash -ex

          wget 
https://aws-tc-largeobjects.s3-us-west-2.amazonaws.com/DEV-AWS-MO-GCNv2/FlaskApp.zip

          unzip FlaskApp.zip

          cd FlaskApp/

          yum -y install python3 mysql

          pip3 install -r requirements.txt

          amazon-linux-extras install epel

          yum -y install stress

          export PHOTOS_BUCKET=${SUB_PHOTOS_BUCKET}

          export AWS_DEFAULT_REGION=<INSERT REGION HERE>

          export DYNAMO_MODE=on

          FLASK_APP=application.py /usr/local/bin/flask run --host=0.0.0.0 --port=80

 

Amazon Linux 2023 user data script: 

          #!/bin/bash -ex

          wget 
https://aws-tc-largeobjects.s3-us-west-2.amazonaws.com/DEV-AWS-MO-GCNv2/FlaskApp.zip

          unzip FlaskApp.zip

          cd FlaskApp/

          yum -y install python3-pip

          pip install -r requirements.txt

          yum -y install stress

          export PHOTOS_BUCKET=${SUB_PHOTOS_BUCKET}

          export AWS_DEFAULT_REGION=<INSERT REGION HERE>

          export DYNAMO_MODE=on

          FLASK_APP=application.py /usr/local/bin/flask run --host=0.0.0.0 --port=80 


#!/bin/bash -ex

wget https://aws-tc-largeobjects.s3-us-west-2.amazonaws.com/DEV-AWS-MO-GCNv2/FlaskApp.zip
unzip FlaskApp.zip
cd FlaskApp/
yum -y install python3-pip
pip install -r requirements.txt
yum -y install stress
export PHOTOS_BUCKET=${SUB_PHOTOS_BUCKET}
export AWS_DEFAULT_REGION=eu-west-3
export DYNAMO_MODE=on
FLASK_APP=application.py /usr/local/bin/flask run --host=0.0.0.0 --port=80 