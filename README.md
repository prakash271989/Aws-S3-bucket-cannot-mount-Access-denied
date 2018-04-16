# Aws-S3-bucket-cannot-mount-Access-denied
I created a S3 bucket and tried to mount s3  in Ec2 Linux instance.   But when trying to mount s3, I got the access denied error message.


I followed the below steps

1) Dependency packages installation
2) IAM user creation
3) s3buckeet creation 

Step 1 :-

Dependency packages inststallations
sudo yum install automake fuse fuse-devel gcc-c++ git libcurl-devel libxml2-devel make openssl-devel

downloaded the current updated s3fs-suse code
git clone https://github.com/s3fs-fuse/s3fs-fuse.git

Installation has done by using below commands
cd s3fs-fuse

./autogen.sh

./configure --prefix=/usr --with-openssl

make

sudo make install

Verified the s3fs path whether the installaiton is complete successfully
which s3fs

Step 2 :-

IAM user creation steps:
goto -IAM - added the user and assigned AmazonS3FullAccess for Provides full access to all buckets via the AWS Management Console.

copied the Access Key and Secret Key ID from IAM 

created the new file called /etc/passwd-s3fs  and pasted the access and security key on the below format.
access key: security key

permission has assigned to /etc/passwd-s3fs file.
chmod 640 /etc/passwd-s3fs


I created the folder in EC2 instnce which is going to mount whith s3bucket.
mkdir mydatafile

created the s3 bucket from aws console page.

Step 3 :-

after that mount the s3bucketin your Ec2 instance using below command.
s3fs your_bucketname -o use_cache=/tmp -o allow_other -o uid=1001 -o mp_umask=002 -o multireq_max=5 /mydatafile

In S3 creation  Set permission ->Manage public permissions -> i just leave as it is(Do not grant public read access to this bucket (Recommended)). If i changed to public i can able to mount the s3 bucket in Ec2 instance using aws owner and ACL user.

