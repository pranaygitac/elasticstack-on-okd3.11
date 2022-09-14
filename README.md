# elasticstack-on-okd3.11
deploying elastic stack on okd 3.11 to monitor cluster metrics

1. Give your okd user cluster admin privledge
oc create clusterrolebinding registry-controller   --clusterrole=cluster-admin --user=pranay

2. login in your user account in console


![image](https://user-images.githubusercontent.com/95764498/190231534-bb8eea0a-a381-466e-8997-57d01f6b33aa.png)

3. create new ptoject using console


![image](https://user-images.githubusercontent.com/95764498/190231245-9f049ad5-e12b-4926-ab29-ddbbd5fe0b44.png)


4. enter in your newly created project , go to storage section and click on create storage
   
![image](https://user-images.githubusercontent.com/95764498/190233969-c95ec353-feb8-4528-9e82-1938a3e5694d.png)


5.create storage for your elasticsearch app


![image](https://user-images.githubusercontent.com/95764498/190235127-a25d786b-3a40-4243-ab2c-fbad2ce4e294.png)



6. click on add to project>import YAML/JSON


![image](https://user-images.githubusercontent.com/95764498/190232899-b3793070-fe5e-4d29-9969-50a75dfd0201.png)


7. create elasticsearch single node cluster by importing elasticsearch-StatefulSet.yaml


![image](https://user-images.githubusercontent.com/95764498/190238423-0f4653e0-f9ce-4b3f-b5bf-bdbe15c4c151.png)


8. create service for elasticsearch app by importing elasticsearch-service.yaml
9. retrive clusterIP for elasticsearch service and fire command curl -u [elastic-user]:[elastic-password] -k http://[clusterIP-for-elasticsearch-service]:9200 to check elasticsearch cluster status
   
   
![image](https://user-images.githubusercontent.com/95764498/190241982-93d76bec-4671-4f14-8d81-e42612a2435d.png)

10. create kibana deployment and service by copying defination from kibana.yaml
11. copy NodePort for kiban-nodeport and paste url in [systemIP]:[kiban-nodeport] fashion in browser to access kibana dashboard
   
   
![image](https://user-images.githubusercontent.com/95764498/190247174-7af04120-dc72-4555-8c67-0c6379df9aa7.png)
   
   
![image](https://user-images.githubusercontent.com/95764498/190251543-11e23ccb-7d19-42a7-a19d-34dd79ffe268.png)

12. create service account "kube-state-metrics" (ref. kube-state-metrics.yaml)



![image](https://user-images.githubusercontent.com/95764498/190254678-5a74f53e-f89c-4a81-ae23-53439280a406.png)

   
13. create cluserrole kube-state-metrics ,  (ref. kube-state-metrics.yaml).
    now clusterrolebind service account "kube-state-metrics" with cluserrole "kube-state-metrics" of other namespaces you want to monitor
    then create deployment and service for kube-state-metrics
    
14. create service account metricbeat and grant it privileged SCC (ref. metricbeat.yaml)


![image](https://user-images.githubusercontent.com/95764498/190273123-a7aba24b-da01-465d-b225-5ce720b128ec.png)

15. create role , clusterrole, rolebinding, cluster role binding , configmaps and deployment for metricbeat (ref. metricbeat.yaml)
16. 







