# Devoir d’applications mobiles

**Matière :** Applications mobiles  
**Date :** 6 novembre 2026

## Objectifs

- Donner les parts de marché d’Android, d’iOS et de HarmonyOS.
- Expliquer la différence entre Android Runtime (ART) et les bibliothèques natives d’Android.

## TAF 1 — Parts de marché d’Android, d’iOS et de HarmonyOS

### 1. Précision sur l’énoncé

L’énoncé mentionne « Android Studio, iOS et HarmonyOS ». **Android Studio est un environnement de développement intégré (IDE)** permettant de créer des applications Android [1]. Pour comparer des systèmes d’exploitation mobiles, le terme retenu ici est donc **Android**. Si le professeur souhaitait une étude des outils de développement, il faudrait définir une autre comparaison.

### 2. Périmètre et méthode

Une part de marché dépend de la période, de la zone géographique et de l’indicateur choisi. Ce devoir utilise une même source pour les trois systèmes : **Counterpoint Research, “Global Smartphone Sales Share by Operating System”**, publication du 31 août 2026 [2].

- **Zone :** monde.
- **Période :** deuxième trimestre 2026, d’avril à juin.
- **Indicateur :** part des ventes de smartphones par système d’exploitation.
- **Consultation :** 6 novembre 2026.

Ces valeurs ne représentent ni la proportion de tous les téléphones déjà en circulation ni une mesure du trafic web. La période retenue est celle du dernier tableau mondial par OS disponible sur la page consultée.

### 3. Résultats

| Système d’exploitation | Part des ventes mondiales de smartphones, T2 2026 | Rang |
| --- | ---: | ---: |
| Android | **75 %** | 1 |
| iOS | **20 %** | 2 |
| HarmonyOS | **5 %** | 3 |
| **Total des catégories publiées** | **100 %** | — |

Source : Counterpoint Research [2]. La source emploie « Harmony » dans son tableau pour désigner HarmonyOS. Ses pourcentages sont présentés arrondis.

### 4. Interprétation

Android domine les ventes mondiales sur ce trimestre, avec environ trois smartphones vendus sur quatre. iOS occupe la deuxième place et HarmonyOS la troisième. Le classement varie selon les pays : la même source attribue à HarmonyOS **24 % des ventes en Chine**, contre **5 % à l’échelle mondiale** [2]. Il faut donc préciser le périmètre avant de comparer des chiffres.

## TAF 2 — Différence entre Android Runtime et les bibliothèques natives

### 1. Android Runtime (ART)

**ART est l’environnement d’exécution du code géré d’Android**, et pas simplement une bibliothèque [3]. Il exécute le format **DEX (Dalvik Executable)**, produit à partir du code des applications, notamment en Java ou en Kotlin.

ART assure notamment l’exécution du bytecode, la gestion des objets et le ramasse-miettes (*Garbage Collector*), qui récupère la mémoire des objets devenus inutilisables. Il fournit également des fonctions de diagnostic [3].

Pour exécuter les méthodes, ART peut combiner **interprétation**, **compilation JIT** (*Just-In-Time*, pendant l’exécution) et **compilation AOT** (*Ahead-Of-Time*, avant l’exécution). Le profil d’utilisation aide à choisir les portions à compiler [4]. Il serait donc inexact de limiter ART à une compilation systématique de toute l’application à l’installation.

### 2. Bibliothèques natives (*Native Libraries*)

Les bibliothèques natives sont des ensembles de fonctions compilées en **code machine**, généralement à partir de C ou de C++. Elles fournissent des services spécialisés au système et aux applications [5].

Exemples dans Android :

| Bibliothèque ou famille | Fonction |
| --- | --- |
| Bionic (`libc`) | Fonctions de base du langage C |
| SQLite | Base de données relationnelle locale |
| OpenGL ES | Rendu graphique 2D et 3D |

Le code natif doit correspondre à l’architecture et à l’ABI ciblées, par exemple ARM64. Le NDK permet de développer des composants C/C++ pour Android [5][7].

### 3. Tableau comparatif

| Critère | ART | Bibliothèques natives |
| --- | --- | --- |
| Nature | Environnement d’exécution du code géré | Fonctions spécialisées en code machine |
| Entrée principale | Bytecode DEX | Instructions compilées pour une ABI |
| Rôle | Exécuter et optimiser les méthodes de l’application | Fournir des services : calcul, stockage, graphismes, etc. |
| Mémoire | Ramasse-miettes pour les objets gérés | Gestion selon les outils et conventions du code natif ; le GC d’ART ne libère pas automatiquement les allocations C/C++ |
| Exemple | Exécuter une méthode Java de l’application | Effectuer un calcul dans une bibliothèque C++ |

La différence porte sur leur **rôle**, et pas uniquement sur leur langage : ART lui-même comporte du code natif [5].

### 4. Comment travaillent-ils ensemble ?

Une application peut appeler une fonction native depuis son code Java ou Kotlin grâce à **JNI (Java Native Interface)** [6]. Par exemple, une application photo peut utiliser du code géré pour son interface et une bibliothèque C++ pour un traitement d’image. ART exécute le code géré ; JNI assure la liaison avec le composant natif.

Les bibliothèques de base Java utilisées avec ART constituent encore une autre notion : elles fournissent des classes et des fonctions au code géré. Elles ne doivent pas être confondues avec l’environnement ART lui-même [5].

## Sources

Toutes les sources ont été consultées le **6 novembre 2026**.

1. Google — [Meet Android Studio](https://developer.android.com/studio/intro).
2. Counterpoint Research — [Global Smartphone Sales Share by Operating System](https://counterpointresearch.com/en/insights/global-smartphone-os-market-share), publication du 31 août 2026, tableau « Global », colonne « Q2 2026 ».
3. Android Open Source Project — [Android runtime and Dalvik](https://source.android.com/docs/core/runtime).
4. Android Open Source Project — [Implement ART just-in-time compiler](https://source.android.com/docs/core/runtime/jit-compiler).
5. Google — [Platform architecture](https://developer.android.com/guide/platform), rubriques « Android runtime » et « Native C/C++ libraries ».
6. Google — [JNI tips](https://developer.android.com/ndk/guides/jni-tips).
7. Google — [Native APIs](https://developer.android.com/ndk/guides/stable_apis).
