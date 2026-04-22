# lab18

# 📱 Lab 18 – Analyse de sécurité d’une application mobile (FireStorm)

## 🛠️ Outils utilisés

* **ADB (Android Debug Bridge)**
* **Frida**
* **JADX (Reverse Engineering)**
* **Émulateur Android**

---

## ⚙️ Étape 1 : Installation de l’application et Vérification des processus avec Frida

Installation de l’APK sur l’émulateur Android via ADB :

```bash
adb install FireStorm.apk
```

```bash
frida-ps -U
```

<p align="center">
  <img src="images/1.png" width="700"/>
</p>

---

## 🧠 Étape 3 : Analyse du code avec JADX

Décompilation de l’application pour comprendre la logique interne.

On identifie une fonction responsable de la génération du mot de passe dans `MainActivity`.

<p align="center">
  <img src="images/step3_jadx_analysis.png" width="700"/>
</p>

---

## 📂 Étape 4 : Analyse du fichier strings.xml

Inspection des ressources pour trouver des informations sensibles :

* Email Firebase
* API Key
* URL de la base de données

<p align="center">
  <img src="images/step4_strings_xml.png" width="700"/>
</p>

---

## ⚡ Étape 5 : Injection avec Frida

Utilisation d’un script Frida pour intercepter et exécuter dynamiquement la fonction de génération du mot de passe :

```bash
frida -U -f com.pwnsec.firestorm -l frida_firestorm.js
```

<p align="center">
  <img src="images/step5_frida_script.png" width="700"/>
</p>

---

## 🔑 Étape 6 : Génération du mot de passe

Le script permet de récupérer dynamiquement le mot de passe Firebase :

<p align="center">
  <img src="images/step6_password_generated.png" width="700"/>
</p>

---

## 🚨 Étape 7 : Récupération du flag

Connexion réussie et récupération du flag final :

<p align="center">
  <img src="images/step7_flag.png" width="700"/>
</p>

---

## ✅ Résultat final

✔ Mot de passe récupéré avec succès
✔ Accès Firebase obtenu
✔ Flag extrait

---

## 🧠 Conclusion

Ce lab démontre l’importance de :

* Ne pas stocker d’informations sensibles dans les ressources
* Protéger le code contre le reverse engineering
* Éviter l’exposition des clés API
* Sécuriser les fonctions critiques contre l’instrumentation dynamique

---

## 🔒 Recommandations

* Utiliser l’obfuscation (ProGuard / R8)
* Stocker les secrets côté serveur uniquement
* Implémenter des mécanismes anti-Frida
* Vérifier l’intégrité de l’application

---

## 👨‍💻 Auteur

**Gomi Mustapha**

---
