## Vault SSH Helper

- Run:
```
docker-compose up -d
```
- Get Vault root token:
```
docker container logs vault
```
- Login to Vault:
```
vault login <token>
```
- Enable SSH Secret Engine:
```
vault secrets enable ssh
```
- Write an admin role:
```
vault write ssh/roles/admin key_type=otp default_user=root cidr_list=0.0.0.0/0
```
- Get OTP:
```
vault write ssh/creds/admin ip=10.0.0.20
```

- Login to SSH server:

```
ssh root@localhost -p 3000
root@localhost's password: <OTP>
```