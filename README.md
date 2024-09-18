# Run Hashicorp Vault in a Nitro Enclave

Courtesy of [Enclaver](https://edgebit.io/enclaver/docs/0.x/guide-vault/).


### Security Benefits:

* Automatic unsealing only possible from the trusted enclave image
* Impossibility of introspecting or reconfiguring the environment inside the enclave
* No shell access to the enclave
* Cryptographic attestation ensures Vault only unseals in a known trusted state.
* Use of AWS KMS for auto-unsealing, with policies that ensure only the genuine Vault image running in an enclave can access the unseal key.

### TODO:

- [ ] Network Segmentation: The current setup uses --net=host, which gives the container full access to the host's network stack.
- [ ] Stop using a privileged container (--privileged flag)
- [ ] IaC: Terraform + Ansible
- [ ] Better manage initial secrets: stop to handle manually sensitive information like KMS key IDs and Vault tokens
- [ ] integrating with a proper certificate authority (not self-signed)
- [ ] Improve Vault internal Configuration (auth, ACLs, etc)
- [ ] TLS everywhere (consul etc)
- [ ] backup and restore procedures for the Vault data.
- [ ] HA multi-node Vault
- [ ] Monitoring and Logging
- [ ] external identity providers
