# Cour 01 : **Introduction**

## 1. **Introduction:**

-   **Definition:**

    > React Native est un framework open-source développé par Facebook qui permet de créer des applications mobiles multiplateformes en utilisant JavaScript et la bibliothèque React. Ce framework est conçu pour faciliter le développement d'applications natives pour les systèmes d'exploitation iOS et Android à partir d'une base de code unique.

-   **Principes de Base de React Native:**

    1. **Utilisation de JavaScript et de React** : React Native utilise JavaScript, le langage de programmation largement connu, et React, une bibliothèque pour la construction d'interfaces utilisateur. Si vous êtes déjà familier avec React pour le développement web, vous trouverez de nombreuses similitudes avec React Native.

    2. **Composants Natifs** : Contrairement aux frameworks hybrides qui utilisent des composants web enveloppés dans une application native, React Native compile les composants écrits en JavaScript vers des composants natifs. Cela permet d'obtenir des performances et une expérience utilisateur plus proches des applications purement natives.

    3. **Single Codebase, Multiple Platforms** : Avec React Native, vous pouvez écrire une seule base de code qui fonctionne sur plusieurs plateformes, ce qui permet de réduire les coûts de développement et de maintenance.

    4. **Hot Reloading** : Cette fonctionnalité permet aux développeurs de voir les résultats de leurs modifications de code en temps réel sans avoir à recompiler l'application entièrement. Cela accélère le processus de développement et le débogage.

-   **Avantages de React Native:**

    -   **Économie de Temps et de Ressources** : En utilisant une seule base de code pour les deux plateformes principales, les développeurs peuvent économiser du temps et des ressources par rapport au développement séparé pour iOS et Android.

    -   **Performance** : Les applications React Native bénéficient d'une bonne performance grâce à l'utilisation de composants natifs.

    -   **Large Communauté et Écosystème** : Étant donné que React Native est open-source, il dispose d'une vaste communauté de développeurs et d'une abondance de bibliothèques et de plugins tiers.

    -   **Support Facebook et Contributions de la Communauté** : Initialement développé et utilisé par Facebook, React Native bénéficie d'un soutien solide et de contributions constantes de la communauté.

## 2. **Installation:`expo-cli`**

> Pour commencer avec React Native, voici les étapes de base pour installer et configurer votre environnement de développement :

-   **Installer Node.js** : React Native nécessite Node.js, donc commencez par installer la dernière version de Node.js.

-   **Installer Expo CLI** : Un outil plus simple et rapide pour démarrer avec React Native, idéal pour les débutants. Vous pouvez installer Expo CLI en utilisant npm :

    ```bash
    npm install -g expo-cli
    npx expo login
    ```

-   **Créer un Nouveau Projet** :

    ```bash
    npx create-expo-app@latest --template blank
    cd MonProjet
    npx expo start
    ```

## 3. **Exemple:**

```jsx
import React from "react";
import { Text, View, Button } from "react-native";
import { useState } from "react";

const YourApp = () => {
    const [count, setCount] = useState(0);

    function handelClick() {
        setCount(count + 1);
    }

    return (
        <View
            style={{
                flex: 1,
                justifyContent: "center",
                alignItems: "center",
            }}
        >
            <Text>{count}</Text>
            <Button title="Click Me" onPress={handelClick} />
        </View>
    );
};

export default YourApp;
```

![alt text](image.png)
