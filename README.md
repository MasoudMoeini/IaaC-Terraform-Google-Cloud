# IaaC-Terraform-Google-Cloud
Clone Repo and configure GCP CLI [Instruction](https://cloud.google.com/sdk/docs/install)
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
To access web applicaton from your local laptop
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
terraform delete
```