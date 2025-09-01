# TP 1 : Manipulation du système de fichiers HDFS

## 1. Création de l'arborescence dans la racine HDFS

```bash
# Créer le répertoire principal BDDC
hdfs dfs -mkdir /BDDC

# Créer les sous-répertoires JAVA et CPP
hdfs dfs -mkdir /BDDC/JAVA
hdfs dfs -mkdir /BDDC/CPP

# Créer les sous-répertoires TPs et Cours sous JAVA
hdfs dfs -mkdir /BDDC/JAVA/TPs
hdfs dfs -mkdir /BDDC/JAVA/Cours

# Créer les sous-répertoires TPs et Cours sous CPP
hdfs dfs -mkdir /BDDC/CPP/TPs
hdfs dfs -mkdir /BDDC/CPP/Cours
```

## 2. Création des fichiers CoursCPP dans le répertoire Cours de CPP

```bash
# Créer les fichiers avec du contenu
echo "Contenu du cours CPP1" | hdfs dfs -put - /BDDC/CPP/Cours/CoursCPP1
echo "Contenu du cours CPP2" | hdfs dfs -put - /BDDC/CPP/Cours/CoursCPP2
echo "Contenu du cours CPP3" | hdfs dfs -put - /BDDC/CPP/Cours/CoursCPP3
```

## 3. Affichage du contenu des fichiers CoursCPP

```bash
hdfs dfs -cat /BDDC/CPP/Cours/CoursCPP1
hdfs dfs -cat /BDDC/CPP/Cours/CoursCPP2
hdfs dfs -cat /BDDC/CPP/Cours/CoursCPP3
```

## 4. Copie des fichiers CoursCPP vers le répertoire Cours de JAVA

```bash
hdfs dfs -cp /BDDC/CPP/Cours/CoursCPP1 /BDDC/JAVA/Cours/
hdfs dfs -cp /BDDC/CPP/Cours/CoursCPP2 /BDDC/JAVA/Cours/
hdfs dfs -cp /BDDC/CPP/Cours/CoursCPP3 /BDDC/JAVA/Cours/
```

## 5. Suppression et renommage dans le répertoire Cours de JAVA

```bash
# Supprimer CoursCPP3
hdfs dfs -rm /BDDC/JAVA/Cours/CoursCPP3

# Renommer CoursCPP1 en CoursJAVA1
hdfs dfs -mv /BDDC/JAVA/Cours/CoursCPP1 /BDDC/JAVA/Cours/CoursJAVA1

# Renommer CoursCPP2 en CoursJAVA2
hdfs dfs -mv /BDDC/JAVA/Cours/CoursCPP2 /BDDC/JAVA/Cours/CoursJAVA2
```

## 6. Création d'un répertoire local avec les fichiers TPs

```bash
# Créer un répertoire local
mkdir local_tps
cd local_tps

# Créer les fichiers TPs localement
echo "Contenu TP1CPP" > TP1CPP
echo "Contenu TP2CPP" > TP2CPP
echo "Contenu TP1JAVA" > TP1JAVA
echo "Contenu TP2JAVA" > TP2JAVA
echo "Contenu TP3JAVA" > TP3JAVA
```

## 7. Copie des fichiers TP CPP vers HDFS

```bash
hdfs dfs -put TP1CPP TP2CPP /BDDC/CPP/TPs/
```

## 8. Copie des fichiers TP JAVA vers HDFS

```bash
hdfs dfs -put TP1JAVA TP2JAVA /BDDC/JAVA/TPs/
```

## 9. Affichage récursif du contenu du répertoire BDDC

```bash
hdfs dfs -ls -R /BDDC
```

## 10. Suppression du fichier TP1CPP du répertoire TPs

```bash
hdfs dfs -rm /BDDC/CPP/TPs/TP1CPP
```

## 11. Suppression du répertoire JAVA avec son contenu

```bash
hdfs dfs -rm -r /BDDC/JAVA
```

## Commandes utiles supplémentaires

Pour vérifier la structure de vos répertoires à tout moment :
```bash
# Lister le contenu d'un répertoire
hdfs dfs -ls /BDDC

# Vérifier l'espace disque utilisé
hdfs dfs -du -h /BDDC

# Vérifier l'état du système de fichiers HDFS
hdfs dfsadmin -report
```
