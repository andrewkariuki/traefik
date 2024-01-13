# Traefik

Configure traefik locally.

## SSH Certificates

To generate SSH keys in a local environment you would need the package _mkcert_

1. Windows installation

   ```powershell
   winget install -e --id FiloSottile.mkcert
   ```

2. Linux installation

   ```bash
   sudo apt install libnss3-tools
   ```

3. macOS installation

   ```bash
   brew install mkcert
   ```

Initialise mkcert

```bash
mkcert -install
```

Create locally-trusted development certificates.

```bash
cd certs
mkcert --cert-file my-certificate.local.crt --key-file my-certificate.local.key *.my-workspace.local
```

## TLS Config

Create a _tls_certificates.yml_ file in the folder conf. Within it outline the various certificates you have generate in the SSH Certificates section. The file will look like this

```yaml
tls:
  certificates:
    - certFile: "/etc/traefik/certs/my-certificate.crt"
      keyFile: "/etc/traefik/certs/my-certificate-key.key"
```
