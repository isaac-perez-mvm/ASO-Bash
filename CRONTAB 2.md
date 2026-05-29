
```sh
# Guardar date Y-M-D en $HOY para poder hacer una carpeta diferente cada dia
HOY=$(date +%Y-%m-%d)

#Vamos a la raiz
cd /
#ls para ver donde esta

# Crear carpeta donde guardar todo esto
DIR="/Informe/$HOY-CRONTAB"
mkdir -p "$DIR"
cd "$DIR"
  
# Creamos un txt de informe
INFORME="$DIR/informe_$HOY.txt"
echo "==========================" > "$INFORME"
echo "     Informe diario       " >> "$INFORME"
echo "          $HOY            " >> "$INFORME"
echo "==========================" >> "$INFORME"
echo "" >> "$INFORME"

#Comandos utiles:
#Porcentaje de uso de almacenamiento
df / | tail -n 1 | tr -s ' ' | cut -d' ' -f5 

#Borrar LOG

#Copia SEGURIDAD

ELIMINAR ARCHIVOS TEMPORALES DE hace x dias

VER SI RED ESTA DISPONIBLE
```
