create iam user 
   Add Permission 
    * ec2fullaccess
    * s3fullaccess
   Security credentials --> create Access key --> Download it 

Create roles 
   Add Permission 
    * ec2fullaccess
    * s3fullaccess

Create ec2 linux os 
   Create Key
   Secutry Group -Premission ssh , http , https

Configure AWS CLI with your credentials
 go to gitdash 
   * Configure AWS CLI with your credentials
       Run the following command:
             aws configure

         Enter AWS Access Key
         Enter AWS Secret Key
         Choose region (e.g., us-east-1)
         Choose output format: json (default)     

Step 2: Fetch EC2 Volumes Data
       Run the following command to get details of all EBS volumes:
             aws ec2 describe-volumes --query "Volumes[*].[VolumeId,State,Size,AvailabilityZone,CreateTime]" --output json > volumes.json
    
Step 3: Convert JSON to CSV
       Now, convert the JSON file to CSV using the following command:        
             aws ec2 describe-volumes --query "Volumes[*].[VolumeId,State,Size,AvailabilityZone,CreateTime]" --output text > volumes.csv

Step 4: Verify File Creation
       Check if the file exists:     
            ls -l volumes.csv

Step 4: Create S3 Bucket
       Run command 
            aws s3 cp ~/volumes.csv s3://Your-Bucket-Name/

YOU WILL SEE
            ✅ If successful, you will see:

             upload: ./volumes.csv to s3://hello123hi/volumes.csv

