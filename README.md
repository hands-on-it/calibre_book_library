# Calibre self hosted server installation steps
##

- Calibre server
- NGINX revers proxy
- Certificates

## How-to

1. Generate rootCA
```bash
   chmod +x gen_cah.sh
   ./gen_ca.sh
```
2. Generate server certificates (use calibre name for files)
```bash
   chmod +x make_certs.sh
   ./make_certs.sh
```

3. Create direcotry for server files
```bash
   mkdir -p /opt/calibre
   mkdir -p /opt/calibre/books
   mkdir -p /opt/calibre/calibre-config
   mkdir -p /opt/calibre/certs
```

4. Copy certificates to build directory
```bash
   cp rootCA.crt /opt/calibre/certs
   copy calibre.crt  calibre.key  /opt/calibre/certs
```

5. Place Dockerfile and docker-compose.yml into /opt/calibre/

e.g.
```bash
   vim Dockerfile
   vim docker-compose.yml
```

6. Run
```bash
   docker compose -f docker-compose.yml up -d
```
7. Wait until Deployment finished
```bash
   docker compose -f docker-compose.yml logs -f gitlab
```


