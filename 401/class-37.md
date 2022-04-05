# Reading Notes 37 -- S3

Amazon S3 is a cloud data storage service that stores objects. Amazon S3 is scalable and there are a variety of storage classes for different performance, durability and availability requirements.

## Storage Details 
- Standard or default
- Standard IA (Infrequent Access) for less frequently accessed data like backups and recovery.
- One Zone IA for very infrequent access but very fast retrieval. 
- Glacier is designed for very long term data and retrieval time of at least 12 hours (but cheaper).

Notes
- S3 data buckets are private be default but permissions can be given in a very granular way.
- S3 Object Lambda allows custom code to process GET requests and Event notifications allow work flow triggering.
- Amazon has monitoring and logging tools to better control how S3 resources are being used.
- Analytics are available for better understanding and allows for optimizing storage.

## How it Works

The items that are stored in S3 are referred to as objects. Buckets are containers for objects. Buckets exist in specific regions and allow for organizing and segregating data.

Keys are used to identify objects within a bucket, each object has a single key. Each object's URI can be accessed by the combination of the web service endpoint, bucket name, key (and optionally a version).

## Other 

S3 access points have dedicated policies to allow for how data can be accessed. Access points are attached to buckets and allow object operations such as get and put.

Permissions can be controlled with IAM for sharing with other developers or via the access control lists. ACLs are now considered outdated and IAM permissions is the preferred method.

S3 can be accessed from the AWS management console or via the command line tool
