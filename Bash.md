# Bash Questions and Answers

## Table of Contents
- [Basics](#basics)
- [Advanced Topics](#advanced-topics)
- [Troubleshooting](#troubleshooting)
- [Resources](#resources)

# Bloc 1 - 'Variables i entrada de dades'
El teu script podria preguntar:
- nom de l’usuari,
- número de dispositius,
- després obtenir la data o el nom de l’equip.

```sh
#!/bin/bash
echo "Eres el usuario: $(whoami)"

fecha=$(date +"%d/%m/%Y")
hora=$(date +"%H:%M")

echo "Hoy es $fecha"
echo "Y son las $hora"
echo "Hoy es $(date)"
#Es lo mismo pero si lo quieres mostrar solo
date
echo "Aquesta maquina es: $(hostname)"
```


# Bloc 2 - 'IF / ELIF / ELSE'
Imagina que treballes en un centre educatiu i vols fer un script que revisi automàticament si un recurs està disponible, si l’usuari té permisos o si una nota és apta. Segons el resultat, l’script ha de mostrar un missatge diferent.
## Ex1
- Comprovar si un número és positiu, negatiu o zero

## Ex2
- Comprovar si un fitxer existeix
- Comprovar si un directori existeix

## Ex3
- Comparació de notes (útil per a l'examen)
```sh
#!/bin/bash

#Comprovar notes
read -p "Quina es la teva edat" edat
read -p "Quina es la teva nota" nota

# Si es mayor de edat i la nota es += 5 aprueba
if [$edat -ge 19] && [$nota -ge 5];then
	echo "Aprovat i major d’edat"


# Si una de las dos no es cumpleix
elif [$edat -le 19] || [$nota -lt 5];then 
	echo "No compleix els requisits"


# I per escenaris no contemplats o si no es posen numeros
else
	echo "Situacio no contemplada"
fi
```

- Comprovar si l'usuari és root
- Condicions múltiples amb AND (&&) i OR (||),  si existeix el fitxer i té permisos”, o “si l’usuari és administració o és root

```sh
#!/bin/bash
#Comprovar si un número és positiu, negatiu o zero

#Comprovar si un fitxer / directori existeix

#Comprovar notes
read -p "Quina es la teva edat" edat
read -p "Quina es la teva nota" nota

if [$edat -ge 19] && [$nota -gt 4];then
	echo "Aprovat i major d’edat"

elif [$edat -le 19] || [$nota -lt 5];then 
	echo "No compleix els requisits"

else
	echo "Situacio no contemplada"
fi
#Comprovar si l'usuari es root (&& ||)
  #si existeix el fitxer i té permisos:

  #si l’usuari és administració o és root


```
