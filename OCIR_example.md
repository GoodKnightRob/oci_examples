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
- Note: images can also be pulled with
  - `docker pull <region-code>.ocir.io/<tenancy-namespace>/repo-name/image-name:tag`
