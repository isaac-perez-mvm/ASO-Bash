
# CRONTAB Tutorial de uso

Lo primero es hacer el .sh

'bloc8_crontab.sh'
```sh
#!/bin/bash
# Guardar date Y-M-D en $HOY para poder hacer una carpeta diferente cada dia
HOY=$(date +%Y-%m-%d)

# Crear carpeta donde guardar todo esto
DIR="/Informe-CS/$HOY-Bloc8_CRONTAB"
mkdir -p "$DIR"
cd "$DIR"

# Creamos un txt de informe
INFORME="$DIR/informe_$HOY.txt"
echo "==========================" > "$INFORME"
echo "     Informe diario       " >> "$INFORME"
echo "          $HOY            " >> "$INFORME"
echo "==========================" >> "$INFORME"
echo "" >> "$INFORME"

# Copia de seguretat diaria de la HOME
echo "Iniciando copia de seguridad..." >> "$INFORME"
echo "" >> "$INFORME"
tar -czf "$DIR/backup_home_$HOY.tar.gz" /home > "$DIR/backup_errors.log"
echo "Copia de seguridad hecha...   " >> "$INFORME"

# Monitoratge del disc, espai ocupat
echo "==========================" >> "$INFORME"
echo "" >> "$INFORME"
echo "Espai del disc:  " >> "$INFORME"
echo "" >> "$INFORME"
df -h >> "$INFORME"
echo "" >> "$INFORME"
echo "==========================" >> "$INFORME"
echo "" >> "$INFORME"

# Neteja de temporals (crea un directori amb script i esborra els fitxers que conte)
DIR_TEMPORALS="/tmp/meu_script_temporals"
mkdir -p "$DIR_TEMPORALS"
# Borra archivos de esa carpeta que lleven más de 24 horas sin modificarse
find "$DIR_TEMPORALS" -type f -mtime +1 -delete

# Informe semanal

echo "==========================" >> "$INFORME"
echo "" >> "$INFORME"
echo "Us mitja de CPU de la setmana:  " >> "$INFORME"
echo "" >> "$INFORME"
uptime | awk -F'load average:' '{ print $2 }' | cut -d, -f3 >> "$INFORME"
echo "" >> "$INFORME"

echo "--------------------------" >> "$INFORME"

echo "Memoria Ram Disponible i Utilizada: " >> "$INFORME"
echo "" >> "$INFORME"
free -h >> "$INFORME"

echo "--------------------------" >> "$INFORME"

echo "" >> "$INFORME"
echo "Espai de disc per particions: " >> "$INFORME"
echo "" >> "$INFORME"

echo "==========================" >> "$INFORME"
echo "" >> "$INFORME"
echo "Temperatura del sistema:" >> "$INFORME"
if command -v sensors &> /dev/null; then
    sensors >> "$INFORME"
else
    # Alternativa directa del kernel si no tienes el comando 'sensors'
    echo "Temperatura del sistema no encontrada" >> "$INFORME"
fi

echo "INFORME DEL $HOY" >> "$INFORME"
```

Posteriormente:

```
crontab -e
```
Cada dia a las 01:30
Min H D M DiaSemana
```
30 1 * * * /home/escritorio/ASO/Scripts/bloc8_crontab.sh
```
<img width="531" height="62" alt="image" src="https://github.com/user-attachments/assets/95218cae-f7f0-42a1-a7a5-131107f9181b" />
