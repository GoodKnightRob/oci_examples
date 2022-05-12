# Setting up OCI cli
Installing Oracle cli

Linux / Unix
```
bash -c "$(curl -L https://raw.githubusercontent.com/oracle/oci-cli/master/scripts/install/install.sh)"
```

on Oracle linux 8 
```
sudo dnf -y install oraclelinux-developer-release-el8
sudo dnf install python36-oci-cli
```

Mac OS
```
brew update && brew install oci-cli
```
Verfiy installation
```
oci --version
```

Have the CLI guide you through the first-time setup process, use the setup config command:
```
oci setup config
```

Copy your oci api key
```
cat .oci/oci_api_key_public.pem 
```

Go to the Oracle cloud site and Paste it into your Profile -> User Settings -> Add API Key

Steps derived from:
- https://docs.oracle.com/en-us/iaas/Content/API/SDKDocs/cliinstall.htm
- https://docs.oracle.com/en-us/iaas/Content/API/SDKDocs/cliconfigure.htm
