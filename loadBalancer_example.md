# Pre-requisite 
- Have a vcn (lb_vcn)
  - with 3 subnets ( lb_subnet, ad1_subnet, ad2_subnet)
- have an Internet Gateway
- Two security lists
  - lb_sl (no rules)
  - default Security list for lb_vcn (port 80, 22 ingress)
- two instances
  - one instance runing in ad1 then other in ad2
    - each running a webservice

# Create a load balancer
- Public Load balancer
- setname
- set vcn to lb_vcn
- set subnet to lb_subnet
- set a load balancer policy (ex. Weighted round robin)
- Select your backendssets (webserveer AD1 & webserver AD2)

# You should now be able to access the apps through the load balancer ip

