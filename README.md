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


5. create elasticsearch single node statefulset by pasting 



