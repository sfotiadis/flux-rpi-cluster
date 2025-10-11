- create gpg key pair
   ```bash
   gpg --full-generate-key
   ```
- export public key to encrypt secrets
   ```bash
   gpg --armor --export <key-id> > gpgkey.pub
   ```
- if there is no private key on the cluster, do as follows:
   ```bash
   gpg --armor --export-secret-keys <key-id> > gpgkey.priv
   kubectl -n flux-system create secret generic sops-gpg \
   --from-file=pgp.asc=gpgkey.priv
   rm gpgkey.priv
   ```
- create a '.sops.yaml' in your root directory with:
   ```bash
   cat <<EOF > .sops.yaml
   creation_rules:
     - path_regex: .*\.enc\.yaml$
       pgp: "<key-id>"
   EOF
   ```
- now you can encrypt your secrets:
   ```bash
   sops -e -i secret.enc.yaml
   ```
- keep in mind that you have to add following lines to the kustomization
   ```bash
   apiVersion: kustomize.toolkit.fluxcd.io/v1
   kind: Kustomization
   ...
   spec:
      ...
      decryption:
         provider: sops
         secretRef:
            name: sops-gpg
   ```
