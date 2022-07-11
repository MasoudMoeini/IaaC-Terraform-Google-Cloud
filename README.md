# IaaC-Terraform-Google-Cloud
Clone Repo and configure GCP CLI [Instruction](https://cloud.google.com/docs/terraform/get-started-with-terraform)
``` 
source ~/.zshrc
```
```
gcloud init --console-only
```
Make sure Compute engine API has been already enabled <br/>
Configur provider
```
gcloud auth application-default login
```
Adding credentials: Create account service and download json key<br/>
run the following command to set the environment varibale for terraform<br/>
```
export GOOGLE_APPLICATION_CREDENTIALS={{path}}
```
Start Running Terraform
```
terraform init 
```
```
terraform plan 
```
```
terraform apply 
```
Connect to the VM with SSH:<br/>
- Go to the VM Instances page.<br/>
- Find the VM with the name flask-vm.<br/>
- In Connect column, click SSH. in upcomming vm terminal Create app.py in flask vm and run it<br/>
```
nano app.py
```
```
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_cloud():
  return 'Hello Cloud!'

app.run(host='0.0.0.0')
```
```
python app.py
curl http://0.0.0.0:5000
```
To access web applicaton from your local laptop add following script to the end of main.tf
```
output "Web-server-URL" {
 value = join("",["http://",google_compute_instance.default.network_interface.0.access_config.0.nat_ip,":5000"])
}
```
``` 
terraform output
```
the response should be like this:<br/>
Web-server-URL = "http://35.232.182.68:5000"
```
terraform destroy
```