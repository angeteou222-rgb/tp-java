# REPONSES - TPB1 Java

**Q1.** java -version affiche Temurin 25.0.4.1 (LTS) pour le JDK par défaut. java lance la machine virtuelle et exécute le bytecode ; javac est le compilateur, fourni seulement par un JDK (un JRE n'a que java).

**Q2.** Après javac, un fichier Bonjour.class apparaît. Il n'est pas lisible dans un éditeur de texte : c'est du bytecode Java, exécuté par la JVM.

**Q3.** En Java, il y a une étape de compilation (javac) avant l'exécution. Elle détecte avant de lancer le programme les erreurs de syntaxe et de types.

**Q4.** Erreur : "class Salut is public, should be declared in a file named Salut.java". Règle : une classe publique doit porter le même nom que son fichier.

**Q5.** Oui, VS Code souligne la faute en direct avant toute exécution (Language Support for Java). En Python, Pylance signale aussi une parenthèse manquante ; la différence est que Python ne bloque qu'au lancement du script.

**Q6.** Java refuse de compiler int x = "texte"; (incompatible types) car le typage est vérifié à la compilation. En Python, x: int = "texte" s'exécute : les annotations de type ne sont pas vérifiées par l'interpréteur.

**Q7.** Le .gitignore Java ignore target/, *.class, .idea/ et .vscode/ ; celui de Python ignore __pycache__/, .venv/ etc. Le dossier target/ joue le même rôle que __pycache__/. On ne versionne pas les fichiers générés car ils se recréent à la compilation, pèsent lourd et provoquent des conflits inutiles.

**Q8.** Les lignes du bloc dependency dans pom.xml (groupId com.google.code.gson, artifactId gson, version) jouent le rôle de pip install requests. La version demandée (2.11.0) se voit dans la balise version.

**Q9.** Maven stocke les bibliothèques dans un cache partagé, ~/.m2. Si dix projets utilisent Gson, il n'est téléchargé et stocké qu'une seule fois.

**Q10.** groupId (organisation), artifactId (nom du projet) et version identifient de façon unique un artefact Maven. Un projet Python simple n'en a pas besoin car il n'est pas publié et pip identifie les paquets par leur seul nom.
**Q11.** public rend la méthode accessible depuis toute autre classe, static l'attache à la classe (appelable sans créer d'objet), double est le type de retour, obligatoire et vérifié. public et static n'ont pas d'équivalent direct en Python (tout y est public par convention).

**Q12.** J'obtiens IllegalArgumentException: La liste est vide, levée par mon propre test. En Python, moyenne([]) lèverait ZeroDivisionError (division par zéro) si on ne teste pas la liste vide : le comportement n'est donc pas le même, sauf si on lève soi-même une exception.

**Q13.** Maven et la JVM cherchent la classe à partir du chemin du fichier, donc le dossier fr/b1/ doit correspondre à package fr.b1;. Python n'a pas de contrainte équivalente pour un simple script.

**Q14.** Avec Gson commenté, mvn compile échoue : "package com.google.gson does not exist" (BUILD FAILURE). En Python, sans requests installé, l'erreur ModuleNotFoundError n'apparaît qu'à l'exécution, au moment du import.

**Q15.** Avec le JDK 21 sur projet-java25 : "release version 25 not supported". La ligne responsable du pom.xml est maven.compiler.release = 25.

**Q16.** JAVA_HOME indique à Maven et aux outils quel JDK utiliser. Les modifications faites avec $env: ou export ne concernent que le processus du terminal courant (et ses enfants) ; rien n'est enregistré dans le système, donc elles disparaissent à la fermeture du terminal.

**Q17.** Migrer coûte du temps et comporte des risques : compatibilité des bibliothèques, tests à refaire, validation, contraintes de production. Un projet ancien, stable et qui fonctionne reste donc souvent sur sa version LTS tant qu'elle est supportée.

**Q18.** En Python : py -3.12 -m venv .venv (Windows) ou pyenv pour installer et choisir une version. Un .venv garde la version de Python avec laquelle il a été créé, donc chaque projet garde la sienne.

**Q19.** Java compilé : plus rapide et erreurs détectées tôt, mais cycle compilation + exécution plus lourd. Python interprété : démarrage immédiat et souple, mais plus lent et erreurs découvertes tard à l'exécution.

**Q20.** C'est le bytecode, exécuté par la JVM qui existe pour chaque système. Il faut installer un JRE ou un JDK (une JVM) sur la machine cible.

**Q21.** Cela compte surtout pour une application de 50 000 lignes : une erreur de type y est difficile à repérer à la main et le compilateur la détecte avant la mise en production. Pour un script de 20 lignes, on la voit en le lançant.

**Q22.** Script qui renomme des fichiers : Python (court, rapide à écrire). Application Android : Java ou Kotlin (langages supportés par la plateforme). Analyse de données : Python (pandas, numpy). Serveur d'une banque : Java (typage strict, robustesse, performances, écosystème d'entreprise).

**Q23.** Identiques dans les deux TP : configuration de Git et SSH, VS Code, .gitignore, dépôt GitHub, README et REPONSES.md. Les outils indépendants du langage se réutilisent d'un projet à l'autre.

## Tableau de synthèse

| Critère | Python | Java |
|---|---|---|
| Exécution (compilé ou interprété) | Interprété | Compilé en bytecode, exécuté par la JVM |
| Commande pour lancer | python script.py | mvn compile exec:java ou java -cp target\classes Main |
| Typage (vérifié quand ?) | À l'exécution | À la compilation |
| Outil de dépendances | pip + venv | Maven |
| Fichier de dépendances | requirements.txt | pom.xml |
| Où sont stockées les bibliothèques | .venv de chaque projet | ~/.m2 (cache partagé) |
| Version du langage par projet | py -3.12 -m venv / pyenv | JAVA_HOME / SDKMAN, release dans le pom |
| Dossier généré à ignorer | __pycache__/ (et .venv/) | target/ |
| Nombre de lignes de moyenne | à compléter selon mon code Python | environ 10 |