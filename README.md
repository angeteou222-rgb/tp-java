# tp-java

TPB1 : préparer un environnement de développement Java (parallèle au TP Python).

## Contenu
- tp-env-java : projet Maven avec la dépendance Gson (fonction moyenne).
- projet-java21 : même projet, compilé avec le JDK 21.
- projet-java25 : programme Java 25 (Main.java), compilé avec le JDK 25.

## Installer le JDK et Maven (Windows)
1. Télécharger Eclipse Temurin (JDK 21 et JDK 25, .msi) sur adoptium.net. Pour le premier, cocher "Set JAVA_HOME" et "Add to PATH" ; pour le second, ne pas les cocher.
2. Télécharger Maven (archive .zip) sur maven.apache.org, la décompresser (ici C:\tools\apache-maven-3.9.9) et ajouter son dossier bin au PATH.
3. Rouvrir PowerShell et vérifier : java -version, javac -version, mvn -version.

## Changer de JDK par projet
Chaque projet contient un fichier env.ps1 qui fixe JAVA_HOME et le PATH pour le terminal courant :

    Set-ExecutionPolicy -Scope Process Bypass
    cd projet-java25
    . .\env.ps1
    java -version
    mvn compile

Le changement ne dure que le temps du terminal. Dans VS Code, déclarer les deux JDK dans java.configuration.runtimes.