# cour 18 :

-   **Description:**

    > L'API `Platform` dans React Native permet de détecter la plate-forme (iOS, Android, Web, etc.) sur laquelle votre application s'exécute. Cela vous permet d'adapter votre code en fonction de la plate-forme, en utilisant des composants, des styles ou des fonctionnalités spécifiques à chaque plate-forme.

    -   L'API `Platform` fournit des informations sur la plate-forme d'exécution et offre des méthodes pour appliquer des comportements spécifiques à chaque plate-forme. C'est particulièrement utile pour gérer les différences entre iOS et Android.

-   **Propriétés:**

    -   **OS** : Une chaîne de caractères indiquant la plate-forme sur laquelle l'application s'exécute (`'ios'`, `'android'`, `'windows'`, `'web'`, etc.).

    -   **Version** : La version du système d'exploitation.

    -   **isTV** : Un booléen indiquant si l'application s'exécute sur une plate-forme de télévision.

-   **Méthodes:**

    -   **select** : Permet de sélectionner des valeurs spécifiques à une plate-forme. Vous pouvez passer un objet avec des clés correspondant aux noms des plates-formes et `Platform.select` retournera la valeur appropriée pour la plate-forme courante.

    -   **isPad** (iOS seulement) : Un booléen indiquant si l'appareil est un iPad.

    -   **isTVOS** (iOS seulement) : Un booléen indiquant si l'appareil est une Apple TV.

-   **Exemple : Détecter la plate-forme**

    ```javascript
    import React from "react";
    import { Text, View, Platform } from "react-native";

    const App = () => {
        return (
            <View>
                <Text>Vous êtes sur {Platform.OS}</Text>
            </View>
        );
    };

    export default App;
    ```

-   **Exemple avec `Platform.select`:**

    ```javascript
    import React from "react";
    import { Text, View, StyleSheet, Platform } from "react-native";

    const styles = StyleSheet.create({
        container: {
            flex: 1,
            justifyContent: "center",
            alignItems: "center",
            backgroundColor: Platform.select({
                ios: "blue",
                android: "green",
                default: "gray", // Valeur par défaut pour les autres plateformes
            }),
        },
        text: {
            fontSize: 20,
            color: Platform.select({
                ios: "white",
                android: "black",
                default: "black",
            }),
        },
    });

    const App = () => {
        return (
            <View style={styles.container}>
                <Text style={styles.text}>
                    Ceci est une application {Platform.OS}
                </Text>
            </View>
        );
    };

    export default App;
    ```
