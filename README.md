# Aws-S3-bucket-cannot-mount-Access-denied
I created a S3 bucket and tried to mount s3  in Ec2 Linux instance.   But when trying to mount s3, I got the access denied error message.


I followed the below steps

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

Verified the s3fs path hether the installaiton is complete
which s3fs

IAM user creation steps:
goto -IAM - added the user and assigned AmazonS3FullAccess for Provides full access to all buckets via the AWS Management Console.

copied the Access Key and Secret Key ID





