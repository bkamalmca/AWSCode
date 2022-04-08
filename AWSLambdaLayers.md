# AWS Lambda Add layer

### Steps to create pandas package in virtual env from EC2/Sagemaker instance  

* Create venv and install pandas  (used python3.7)
```
  mkdir python  
  cd python  
  python3 -m venv env  
  source env/bin/activate  
  python --version  
  pip3 install pandas
```
  
* Create sub folder python to copy only site packages - due to lambda 250 MB size limit uncompressed    
````
  cd python  
  cp -r ../env/lib/python3.7/site-packages/* .
````  

* Zip the directory and copy to s3  
 ````
  zip -r pandas_layer.zip python 
  aws s3 cp pandas_layer.zip s3://XXX-s3/lambda-layers/
````

* Add layers to Lambda function - Python3.7 runtime

* The function completed successfully with python module

* To install zip in EC2 
```
  sudo yum install zip
```




### Another approach is to use the data wrangler package for pandas library

* Used the AWSDataWrangler in Add Layer and tried running pandas, it worked and was an easy step.  

* For Details, https://aws-data-wrangler.readthedocs.io/en/stable/install.html
