# cour 04 : **`style`**

## 1. **Styles en Ligne:**

-   **Description:**

    > Les styles en ligne dans React Native sont définis directement dans les composants en utilisant l'attribut `style`. C'est une méthode rapide pour appliquer des styles, idéale pour le prototypage ou les modifications rapides. Cependant, elle peut devenir difficile à maintenir dans les grandes applications.

-   **Syntaxe:**

    ```jsx
    <Component
        style={{
            propCSSValide: valeur,
        }}
    ></Component>
    ```

    -   L'attribut `style` prend un objet JavaScript contenant les propriétés CSS adaptées à React Native.

    -   Les noms des propriétés sont en `camelCase` plutôt qu'en kebab-case, et certaines propriétés CSS ne sont pas prises en charge ou ont des noms différents.

-   **Exemple:**

    ```jsx
    import React from "react";
    import { View, Text } from "react-native";

    const App = () => {
        return (
            <View
                style={{
                    flex: 1,
                    justifyContent: "center",
                    alignItems: "center",
                }}
            >
                <Text style={{ fontSize: 20, color: "blue" }}>
                    Bonjour, le monde !
                </Text>
            </View>
        );
    };

    export default App;
    ```

## 2. **StyleSheet**

-   **Description:**

    > `StyleSheet` est une méthode recommandée pour définir des styles dans React Native. Elle permet de créer un objet de styles séparé du composant, ce qui améliore la lisibilité et la maintenabilité du code. `StyleSheet` offre de meilleures performances par rapport aux styles en ligne, car les styles sont encapsulés et optimisés en interne.

-   **Syntaxe:**

    ```jsx
    import { StyleSheet } from "react-native";

    <Component style={styles.nomDeStyle}></Component>;

    const styles = StyleSheet.create({
        nomDeStyle: {
            propCSSValide: valeur,
        },
    });
    ```

    -   Pour utiliser `StyleSheet`, vous devez l'importer depuis `react-native` et créer un objet de styles en utilisant `StyleSheet.create`.

-   **Exemple:**

    ```jsx
    import React from "react";
    import { View, Text, StyleSheet } from "react-native";

    const App = () => {
        return (
            <View style={styles.container}>
                <Text style={styles.text}>Bonjour, le monde !</Text>
            </View>
        );
    };

    const styles = StyleSheet.create({
        container: {
            flex: 1,
            justifyContent: "center",
            alignItems: "center",
        },
        text: {
            fontSize: 20,
            color: "blue",
        },
    });

    export default App;
    ```

### RQ : **Fichiers de Style Externes**

-   Vous pouvez également conserver vos styles dans des fichiers séparés pour une meilleure organisation, surtout dans les grands projets.

-   **Exemple:**

    -   **styles.js**

        ```jsx
        import { StyleSheet } from "react-native";

        export default const  styles =  StyleSheet.create({
            container: {
                flex: 1,
                justifyContent: "center",
                alignItems: "center",
            },
            text: {
                fontSize: 20,
                color: "blue",
            },
        });
        ```

    -   **App.js**

        ```jsx
        import React from "react";
        import { View, Text } from "react-native";
        import styles from "./styles";

        const App = () => {
            return (
                <View style={styles.container}>
                    <Text style={styles.text}>Bonjour, le monde !</Text>
                </View>
            );
        };

        export default App;
        ```
