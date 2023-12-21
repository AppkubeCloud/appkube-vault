# Vault deployment
Deployment (Char version: 0.27.0, App version: 1.15.2)
- helm repo add hashicorp https://helm.releases.hashicorp.com
- helm install vault hashicorp/vault --version 0.27.0 -n vault --create-namespace
- Auto eks unseal is enabled and uses aws kms key
-- KMS -> Customer managed keys -> Key ID: 0f02a237-2bf7-4396-b4fa-0c855fd7f7d7
-- Alias vaultunseal

To access UI, use port forward
- kubectl port-forward vault-0 8200:8200 -n vault 

Vault volume on AWS
- EC2 -> Volumes -> vol-0db5984a7f9d77c4d

Unseal command
- $ kubectl -n vault exec -ti vault-0 -- vault operator unseal # ... Unseal Key 1 
- $ kubectl -n vault exec -ti vault-0 -- vault operator unseal # ... Unseal Key 2 
- $ kubectl -n vault exec -ti vault-0 -- vault operator unseal # ... Unseal Key 3 

aws unseal configuration
https://developer.hashicorp.com/vault/docs/configuration/seal/awskms#awskms-example
