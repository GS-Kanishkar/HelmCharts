# HelmCharts

# Without Helm

I was trying to deploy the nginx image for dev , qa and prod

for dev i was trying 1 replicas
for QA  i was trying 2 replicas
for Prod i was trying 3 replicas

I had 3 folders and inside all i have 3 deploy and 3 service yaml files
If i want to update anything then i have to update all the files and apply these files again

![image](https://github.com/user-attachments/assets/1103f94a-410e-4a66-bb0d-172aa724b292)


![image](https://github.com/user-attachments/assets/d559512c-a4e7-455c-99db-5c0b86661978)

![image](https://github.com/user-attachments/assets/632356ec-b696-44d2-b52c-2682a1f43e60)

![image](https://github.com/user-attachments/assets/a008f0b7-fc8e-4918-86b8-e8d2bef9a72c)

![image](https://github.com/user-attachments/assets/b388a13b-36d7-471f-8a8b-c3f0b1c7c912)

![image](https://github.com/user-attachments/assets/d87c62a7-2431-4519-874b-b03cf21b2eb9)




#   With Helm

With helm for same 3 environments we can create only 1 deploy and 1 service file with placeholders
and we can specify the environment specific details on the environment values yaml files

```
helm create my-helm
```

```
my-helm/
├── charts/          # Dependencies (sub-charts)
├── templates/       # Kubernetes YAML templates
│   ├── deployment.yaml  # Deployment template
│   ├── service.yaml     # Service template
│   ├── ingress.yaml     # (Optional) Ingress template
│   ├── _helpers.tpl     # Template helpers (for names, labels, etc.)
├── values.yaml      # Default configuration values
├── Chart.yaml       # Chart metadata (name, version, etc.)
├── README.md        # Chart documentation
```
![image](https://github.com/user-attachments/assets/14eb2f70-40d1-4d83-8137-7ae920bd40eb)

our files for the helm

![image](https://github.com/user-attachments/assets/b9cc8c74-b779-4955-b3c9-bfc1df2b0893)

helm install

`` helm install dev-nginx ./my-helm -f my-helm/Values-dev.yaml
``
![image](https://github.com/user-attachments/assets/89b8cfc5-1fbb-4e65-98a5-8f7e055a60c5)


helm list

![image](https://github.com/user-attachments/assets/82c3e21b-f1d6-4366-9db6-4cde08d68367)

helm install qa
![image](https://github.com/user-attachments/assets/6bf70ea2-5d0e-48e2-a064-3a99d3adc8dc)

helm install prod
![image](https://github.com/user-attachments/assets/7d56729e-f330-4efa-85a8-4c6c7b8e00c3)

helm list 
3 versions is created

![image](https://github.com/user-attachments/assets/eba1e1fd-fa82-44e6-a20e-899b54caf754)

kubectl get all
![image](https://github.com/user-attachments/assets/899be74d-ed4d-4c4c-a36e-7bd7a3abbc46)


updated dev image to busybox

![image](https://github.com/user-attachments/assets/606af8c2-f608-4f30-8df9-ea21eec13e25)

![image](https://github.com/user-attachments/assets/c703c596-58be-48a3-b63b-7b8f9a9cae4a)

![image](https://github.com/user-attachments/assets/6e1e5c2e-dac2-4506-b9b8-b4a173b739f2)



helm upgrade

![image](https://github.com/user-attachments/assets/5e509c75-21ef-4488-bee5-3add74e91034)

kubectl get all
it deleting the nginx pod and creating the httpd image
![image](https://github.com/user-attachments/assets/ad7109ad-d87b-484a-b797-4a290ed868ad)

localhost:80
![image](https://github.com/user-attachments/assets/403c2323-f8ee-403f-bfe2-19521a6bf346)


helm rollback
![image](https://github.com/user-attachments/assets/3a2be493-8535-44e3-a251-fc66d5147e3e)


localhost80
![image](https://github.com/user-attachments/assets/4807d888-0554-4adb-8de0-b0da87c982c9)

helm history
easily we can track

![image](https://github.com/user-attachments/assets/3c4d7582-0ace-40a1-a054-42e91a9942ec)

helm uninstall
it will delete all the resources

![image](https://github.com/user-attachments/assets/c03956ef-c33b-4e5a-8446-46354dd8adcf)


helm uninstall all

![image](https://github.com/user-attachments/assets/311d6ab5-09eb-4876-a810-46603d7a790f)

kubectl get all

![image](https://github.com/user-attachments/assets/982dd0b6-38f6-48bb-a891-fea461644b72)


