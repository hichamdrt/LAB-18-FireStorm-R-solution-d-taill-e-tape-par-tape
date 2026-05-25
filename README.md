# LAB-18-FireStorm-R-solution-d-taill-e-tape-par-tape

# 🔥 LAB 18 — FireStorm

**Domaine :** Cybersecurity / Reverse Engineering / Mobile Security

---

# 🎯 Objectif du laboratoire

Ce laboratoire a pour objectif d’analyser une application Android afin de :

* identifier des informations sensibles ;
* extraire un mot de passe caché ;
* utiliser Frida pour l’analyse dynamique ;
* interagir avec des composants Firebase ;
* récupérer le FLAG final de l’application.

L’analyse combine des techniques de :

* reverse engineering Android ;
* instrumentation dynamique ;
* automatisation Python ;
* inspection de configurations Firebase.

---

# 🛠️ Outils utilisés

| Outil                   | Fonction                             |
| ----------------------- | ------------------------------------ |
| Jadx-GUI                | Analyse statique de l’APK            |
| Frida                   | Instrumentation dynamique            |
| Python                  | Automatisation et interaction réseau |
| Android Emulator API 30 | Environnement Android                |

---

# 🔹 Étape 1 — Préparation de l’environnement

La première étape consiste à préparer l’environnement Android utilisé pour le laboratoire.

Les opérations réalisées incluent :

* démarrage de l’émulateur Android ;
* installation de l’application FireStorm ;
* lancement de l’application cible.

Cette étape permet de vérifier que l’application fonctionne correctement avant l’analyse statique et dynamique.

## Actions réalisées

* ouverture de l’émulateur Android API 30 ;
* installation de l’APK ;
* exécution de l’application FireStorm.

📸 **Preuve :**

<img width="245" height="476" alt="image" src="https://github.com/user-attachments/assets/8e0f3d54-0d56-4b04-a3df-f6af292d7f79" />

---

# 🔹 Étape 2 — Analyse statique avec Jadx

L’APK est ensuite ouvert dans **Jadx-GUI** afin d’analyser le code Java généré.

L’analyse permet de :

* explorer la structure de l’application ;
* identifier les activités principales ;
* rechercher des chaînes sensibles ;
* localiser les méthodes critiques.

---

## Analyse de `MainActivity`

L’étude du fichier :

```text id="t4m8vp"
MainActivity
```

permet d’identifier une méthode nommée :

```text id="r9x2qd"
Password()
```

Cette méthode semble impliquée dans la gestion ou la validation du mot de passe utilisé par l’application.

---

## Exploration de `strings.xml`

Le fichier :

```text id="v5k1we"
strings.xml
```

contient plusieurs informations sensibles :

* clés Firebase ;
* endpoints réseau ;
* constantes utilisées par l’application.

Cette étape permet de préparer l’analyse dynamique et l’automatisation Python.

📸 **Preuve :**

<img width="790" height="341" alt="image" src="https://github.com/user-attachments/assets/e4a2d8ad-b741-4c52-8e9d-5040828df6de" />

---

# 🔹 Étape 3 — Analyse dynamique avec Frida

Après l’analyse statique, Frida est utilisé afin d’intercepter dynamiquement certaines méthodes Java.

---

## Hook de la méthode `Password()`

Un script Frida est développé afin de :

* intercepter l’appel de la méthode ;
* afficher les valeurs manipulées ;
* observer le comportement interne de l’application.

Le hook permet d’analyser l’exécution en temps réel sans modifier l’APK original.

---

## Exécution du script

Le script Frida est injecté dans l’application depuis l’émulateur Android.

Cette étape permet de :

* récupérer les données traitées dynamiquement ;
* observer les appels internes ;
* extraire des informations utiles à la récupération du FLAG.

📸 **Preuve :**

<img width="887" height="467" alt="image" src="https://github.com/user-attachments/assets/e4239b76-dbb5-4fb4-b51a-a00af105fd8d" />

---

# 🔹 Étape 4 — Analyse Firebase

Les informations récupérées dans :

```text id="j3n7yb"
strings.xml
```

sont ensuite utilisées afin d’analyser la configuration Firebase de l’application.

L’analyse porte notamment sur :

* les clés API ;
* les endpoints Firebase ;
* les paramètres de configuration réseau ;
* les ressources accessibles.

Cette étape permet d’identifier les éléments nécessaires à l’interaction automatisée avec le backend Firebase.

---

# 🔹 Étape 5 — Script Python et récupération du FLAG

À partir des informations extraites précédemment, un script Python est développé afin d’interagir avec Firebase.

Le script permet de :

* envoyer des requêtes au backend ;
* récupérer les données nécessaires ;
* automatiser certaines interactions ;
* obtenir le FLAG final.

---

# ✅ Résultat obtenu

Le laboratoire a permis de :

* analyser statiquement une application Android ;
* identifier une méthode sensible ;
* utiliser Frida pour l’analyse dynamique ;
* extraire des informations Firebase ;
* automatiser les requêtes avec Python ;
* récupérer le FLAG final de l’application.

📸 **Résultat :**

<img width="1057" height="296" alt="image" src="https://github.com/user-attachments/assets/ecccb343-5445-4bd3-ae8b-920a8968c3c9" />

---

# 📌 Conclusion

Ce laboratoire démontre l’intérêt de combiner plusieurs approches complémentaires :

* analyse statique avec Jadx ;
* instrumentation dynamique avec Frida ;
* automatisation Python ;
* inspection des configurations Firebase.

L’étude met également en évidence l’importance de :

* protéger les informations sensibles dans les APK ;
* éviter l’exposition de configurations Firebase ;
* limiter les données accessibles côté client ;
* sécuriser les mécanismes d’authentification et de validation.

L’ensemble des manipulations réalisées dans ce laboratoire reste limité à un environnement pédagogique et contrôlé.
