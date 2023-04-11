# AWS-Cloudfront-cache-invalidation

This code will automate object invalidation in the Cloudfront cache using a lambda function that executes upon creation of object in S3.

The use case is a personal brand page that needs to be updated upon changes.  Overwriting the index.html file in my S3 bucket will allow for immediate invalidation and updating of the cache while keeping the default TTL.  The first 1000 invalidations per month are free in AWS.  When this Time-To-Live (TTL) frame elapses, the network consults the origin server and replaces cached copy with the new version. A largerer TTL allows better performance while a smaller TTL updates content faster but reduces page performance (due to multiple cache misses).   By using AWS Lambda, we can execute the invalidations while keeping the higher TTL, thus keep a page responsive but updating when a new index.html page is uploaded.
