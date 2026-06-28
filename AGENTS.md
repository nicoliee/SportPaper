# SportPaper - Workflows

## Flujo local (testing rápido)

Para probar cambios en un servidor sin regenerar patches:

```bash
# Compilar solo el server (más rápido que build completo)
mvn install -pl SportPaper-Server -am

# El JAR queda en:
#   SportPaper-Server/target/sportpaper-1.8.8-R0.1-SNAPSHOT.jar
```

Copiás ese JAR a la carpeta de tu servidor y lo ejecutás.

## Flujo de patches (para commitear cambios)

Cuando los cambios ya estén listos:

```bash
# 1. Commit en SportPaper-Server (adentro del sub-repo)
git -C SportPaper-Server add -A
git -C SportPaper-Server commit -m "descripción del cambio"

# 2. Regenerar patches desde ese commit
./sportpaper rebuild

# 3. Commitear los patches en el repo raíz
git add patches/
git commit -m "feat: descripción del cambio"
git push
```

Cualquiera que clone el fork puede hacer `./sportpaper build` y obtener el JAR con los cambios.
