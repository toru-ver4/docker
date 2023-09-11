# libjxl

## Build

```powershell
docker build -t takuver4/libjxl:v0.9.0 .
# docker build -t takuver4/libjxl:v0.9.0.0 .
```

## Push

```powershell
docker push takuver4/libjxl:v0.9.0
# docker push takuver4/libjxl:v0.9.0.0
```

## RUN

### docker run

```powershell
docker run -it -P --name libjxl -v C:\Users\toruv\OneDrive\work\sample_code:/work/src --rm takuver4/libjxl:v0.9.0
# docker run -it -P --name libjxl -v C:\Users\toruv\OneDrive\work\sample_code:/work/src --rm takuver4/libjxl:v0.9.0.0 /bin/bash
```

### docker compose

```powershell
docker-compose up -d
```
