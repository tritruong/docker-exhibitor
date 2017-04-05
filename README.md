Runs [Exhibitor](https://github.com/Netflix/exhibitor)-managed [ZooKeeper](http://zookeeper.apache.org/) instance using S3 for automatic node discovery.

Available on the Docker Index as [tritruongtr/zookeeper-exhibitor](https://index.docker.io/u/tritruongtr/zookeeper-exhibitor/):

    docker pull tritruongtr/zookeeper-exhibitor

### Versions
* Exhibitor 1.5.6
* ZooKeeper 3.4.9

### Usage
The container expects the following environment variables to be passed in:

* `HOSTNAME` - addressable hostname for this node (Exhibitor will forward users of the UI to this address)
* `S3_BUCKET` - (optional) bucket used by Exhibitor for backups and coordination
* `S3_PREFIX` - (optional) key prefix within `S3_BUCKET` to use for this cluster
* `AWS_ACCESS_KEY` - (optional) AWS access key ID with read/write permissions on `S3_BUCKET`
* `AWS_SECRET_KEY` - (optional) secret key for `AWS_ACCESS_KEY_ID`
* `AWS_REGION` - (optional) the AWS region of the S3 bucket
* `HTTP_PORT` - (optional) Port for the HTTP Server. Default is: 8080
* `CLIENT_PORT` - (optional) The Exhibitor client port. Default is: 2181
* `CONNECT_PORT` - (optional) The Exhibitor connect port. Default is: 2888
* `ELECTION_PORT` - (optional) The Exhibitor election port. Default is: 3888
* `JAVA_OPTS` - JVM parameter, E.g: "-Xms512m -Xmx1G"


Starting the container:

    docker run -p 8181:8181 -p 2181:2181 -p 2888:2888 -p 3888:3888 \
        -e S3_BUCKET=<bucket> \
        -e S3_PREFIX=<key_prefix> \
        -e AWS_ACCESS_KEY_ID=<access_key> \
        -e AWS_SECRET_ACCESS_KEY=<secret_key> \
        -e HOSTNAME=<host> \
        -e JAVA_OPTS="-Xms512m -Xmx1G"
        tritruongtr/zookeeper-exhibitor
