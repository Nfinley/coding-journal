# Scripts:

A script to add images to an S3 bucket:

```
#!/usr/bin/env bash

BUCKET=$1

cd ~/Documents/beacon_images
# stackline-product-images/client
#FOLDER=~/Documents/beacon_images
echo "$PWD"
echo "ARG = $BUCKET"
for image in *
do
   echo "$image"
   aws s3 cp "$image" "s3://$BUCKET/$image"
   mv "$image" ~/Documents/finished_beacon_images/
done
```
