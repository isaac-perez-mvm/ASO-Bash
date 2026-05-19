
# CRONTAB Tutorial de uso

Lo primero es hacer el .sh

'bloc8_crontab.sh'
```sh
#!/bin/bash
# Crear carpeta donde guardar todo esto
# Guardar date Y-M-D en $HOY para poder hacer una carpeta diferente cada dia
HOY=$(date +%Y-%m-%d)

# Directorio donde se metera todo
DIR="/home/Informe-CS/$HOY-Bloc8_CRONTAB"
mkdir -p "$DIR"

cd /home
mkdir (si no existe) Informe-CS 
cd Informe-CS
mkdir $HOY-Bloc8_Crontab

# Copia de seguretat diaria de la HOME

# Monitoratge del disc, espai ocupat

# Neteja de temporals (crea un directori amb script i esborra els fitxers que conte)

# Informe semanal

echo "Us mitja de CPU de la setmana: $mediacpu"
echo "Memoria Ram Disponible: "
echo "Memoria Ram Utilizada: "
echo "Espai de disc per particions: "
echo "Temperatura del sistema: "
```

Posteriormente:

```
crontab -e
```

```
* * * * * /home/escritorio/ASO/Scripts/bloc8_crontab.sh
```
