# cour 01 : **Introduction à React Navigation:**

## 1. **Introduction:**

-   **Définition:**

    > **React Navigation** est une bibliothèque de navigation pour les applications React Native. Elle permet aux développeurs de créer des interfaces utilisateur avec des transitions fluides et des interactions intuitives. La bibliothèque offre un ensemble de composants et de fonctions permettant de gérer la navigation entre les écrans, qu'il s'agisse de navigation par pile (stack navigation), par onglets (tab navigation), ou par tiroir (drawer navigation).

## 2. **Installation :**

-   **installation:**

    ```bash
    npm install @react-navigation/native
    npx expo install react-native-screens react-native-safe-area-context
    ```

-   **configuration :** dans `App.js`

    ```js
    import * as React from "react";
    import { NavigationContainer } from "@react-navigation/native";

    export default function App() {
        return (
            <NavigationContainer>
                {/* Rest of your app code */}
            </NavigationContainer>
        );
    }
    ```
