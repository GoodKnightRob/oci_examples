# Oracle Registry Service to store docker images / application artifacts
To use the registry service the user is either a part of the admin group or a part of a group which a policy grants the
appropiate permission

example policies:
>allow group acme-viewers to inspect repos in tenancy
>allow grpup acme-managers to manage repos in tenancy


Pre-requisite:
- Auth token ( to create one go to Identity -> Domains -> Default domain -> Users -> (select a user) -> Auth tokens

Steps
- In the OCI console go to OCIR - > Registry -> create repository
- Log into OCIR
  - `docker login <region-code>.ocir.io <tenancy_namespace>/<username> <Auth-token>`
- Find the image in your local machine and tag it in the format
  - `docker images`
  - `docker tag <docker image id> <region-code>.ocir.io/<tenancy-namespace>/<repos-name>/<image-name>:<tag>`
- Push your tagged image to OCIR
  - `docker push iad.ocir.io/username/repo-name/image-name`

Pulling the image
- Note: images can also be pulled with
  - `docker pull <region-code>.ocir.io/<tenancy-namespace>/repo-name/image-name:tag`

# Pulling the image from Registry for Kubernetes Deployments

Ensure cluster is up
`kubectl cluster-info`

Create Docker registry secret and use Auth token
  - `kubectl create secret docker-registry <secret-name> --docker-server=<region-code>.ocir.io --docker-username='<tenancy-namespace>/<oci-username>' --docker-password='<oci-auth-token' --docker-email=`<email-address>'`



Specify the image to pull from OCIR in your yaml file
>sample.yaml
```
apiVersion: v1
kind: Pod
metadata:
  name: image_name
spec:
  containers:
  - name: name
    image: iad.ocir.io/goodknightrob/reponame/image-name:tag
    imagePullPolicy: Always
    ports:
    - name: name
      containerPort: 8080
      protocol: TCP
  imagePullSecrets:
    - name: ocisecret
```
  
Now lets deploy
`kubectl apply -f sample.yaml`
 
We can get additional details on the pod with:
`kubectly get pods -o wide`
`kubectl descreibe pods <name of pod>
