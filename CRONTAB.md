
# CRONTAB Tutorial de uso

Lo primero es hacer el .sh

'bloc8_crontab.sh'
```sh
#!/bin/bash
# Guardar date Y-M-D en $HOY para poder hacer una carpeta diferente cada dia
HOY=$(date +%Y-%m-%d)

# Crear carpeta donde guardar todo esto
DIR="/home/Informe-CS/$HOY-Bloc8_CRONTAB"
mkdir -p "$DIR"
cd "/home/Informe-CS/$HOY-Bloc8_CRONTAB"

# Creamos un txt de informe
INFORME="$DIR/informe_$HOY.txt"
echo "========================" > "$INFORME"
echo "     Informe diario     " >> "$INFORME"
echo "          $HOY          " >> "$INFORME"
echo "========================" >> "$INFORME"


# Copia de seguretat diaria de la HOME
echo "Iniciant copia de seguretat..."
tar -czf "$DIR/backup_home_$HOY.tar.gz" /home> "$DIR/backup_errors.log"

# Monitoratge del disc, espai ocupat

# Neteja de temporals (crea un directori amb script i esborra els fitxers que conte)
TMP="/tmp"
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
