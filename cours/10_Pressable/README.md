# cour 10 :**La composante `Pressable`**

-   **Description:**

    > La composante `Pressable` en React Native est utilisée pour détecter les interactions utilisateur telles que les pressions, les maintiens et les relâchements. `Pressable` est un composant polyvalent et léger, introduit pour remplacer des composants comme `TouchableOpacity`, `TouchableHighlight`, etc., avec plus de flexibilité.

    -   `Pressable` permet de définir des styles et des comportements spécifiques en fonction de l'état d'interaction (pressé, maintenu, etc.). C'est un composant de base qui peut être utilisé pour construire des boutons, des liens ou tout autre composant interactif.

-   **Syntaxe:**

    ```javascript
    import { Pressable } from "react-native";

    <Pressable
        onPress={() => {
            // Action à effectuer lorsque l'utilisateur appuie sur le composant
        }}
        style={({ pressed }) => [
            {
                backgroundColor: pressed ? "rgb(210, 230, 255)" : "white",
            },
            styles.wrapperCustom,
        ]}
    >
        <Text style={styles.text}>Press Me</Text>
    </Pressable>;
    ```

-   **Propriétés principales:**

    -   `onPress`: Callback exécuté lorsqu'une pression est détectée.
    -   `onPressIn`: Callback exécuté lorsque la pression commence.
    -   `onPressOut`: Callback exécuté lorsque la pression se termine.
    -   `onLongPress`: Callback exécuté lorsqu'une longue pression est détectée.
    -   `style`: Permet de définir les styles en fonction de l'état d'interaction.

-   **Exemple:**

    ```javascript
    import React from "react";
    import { Pressable, StyleSheet, Text, View } from "react-native";

    const App = () => {
        return (
            <View style={styles.container}>
                <Pressable
                    onPress={() => alert("Pressed!")}
                    style={({ pressed }) => [
                        {
                            backgroundColor: pressed
                                ? "rgb(210, 230, 255)"
                                : "white",
                        },
                        styles.button,
                    ]}
                >
                    <Text style={styles.text}>Press Me</Text>
                </Pressable>
            </View>
        );
    };

    const styles = StyleSheet.create({
        container: {
            flex: 1,
            justifyContent: "center",
            alignItems: "center",
        },
        button: {
            padding: 10,
            borderRadius: 5,
            borderWidth: 1,
            borderColor: "black",
        },
        text: {
            fontSize: 16,
        },
    });

    export default App;
    ```
