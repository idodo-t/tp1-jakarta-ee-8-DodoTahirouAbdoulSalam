# Utilisation de l'IA dans le TP 1

Assistant utilisé : Claude (Anthropic)

## Utilisation 1 : `beans.xml` au mauvais endroit

**Problème rencontré :** Le professeur a signalé que `beans.xml` devait être dans `resources` et non dans `webapp`. Mon fichier était dans `src/main/webapp/WEB-INF`.

**Raison de l'utilisation de l'IA :** Je voulais le déplacer sans perdre l'historique Git et être sûr du dossier exact.

**Prompt utilisé :**
> Le professeur dit : « beans.xml devrait être dans resources pas dans webapp ». Comment corriger ?

**Réponse de l'IA :**
> Déplacer le fichier vers `src/main/resources/META-INF/beans.xml`, puis `git add -A`, `git commit` et `git push`.

**Ce que j'ai appris :** Maven traite tout le contenu de `src/main/resources` comme des ressources de l'application, et la configuration CDI (`beans.xml`) va dans `META-INF`. Git a détecté un simple déplacement (rename 100 %, contenu inchangé). Commit `66eb85b`.

## Utilisation 2 : Version de Java dans le `pom.xml`

**Problème rencontré :** Le professeur a signalé une « mauvaise version de Java ». Mon `pom.xml` avait `maven.compiler.release` = 21, Jakarta EE 11.0.0 et PrimeFaces 16.0.0, avec un JDK Temurin 21.

**Raison de l'utilisation de l'IA :** L'énoncé demande de vérifier les versions sans donner de numéro, et je ne savais pas laquelle était attendue.

**Prompt utilisé :**
> Mon `pom.xml`, le résultat de `java -version` et la remarque du professeur : quelle version de Java faut-il ?

**Réponse de l'IA :**
> Payara 7 supporte JDK 21 et JDK 25 (21 au minimum), donc `release` = 21 est valide. Il faut vérifier que le JDK d'IntelliJ et le JRE de la configuration Payara sont aussi en 21.

**Ce que j'ai appris :** La version de Java du `pom.xml` doit être alignée avec le JDK installé, celui d'IntelliJ et de la configuration Payara, et les versions supportées par le serveur.

## Ce que j'ai fait moi-même

- Dépôt GitHub, projet Maven, copie du TP 0.
- Record `LlmInteraction`.
- Intégration du code du professeur pour `JsonAdapterPourGemini` et `RequeteException`.
- Tests, dont les 2 erreurs provoquées volontairement et le retour avec `git restore`.