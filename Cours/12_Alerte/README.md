# cour 12 : **API `Alert`:**

-   **Description:**

    > Le module `Alert` de React Native est utilisé pour afficher des boîtes de dialogue d'alerte à l'utilisateur. Ces alertes sont souvent utilisées pour informer l'utilisateur de quelque chose important, demander une confirmation, ou recueillir une réponse simple. L'API `Alert` est très flexible et permet de configurer le titre, le message et les boutons de l'alerte.

-   **Syntaxe:**

    ```jsx
    import { Alert } from "react-native";

    Alert.alert(
        "Title",
        "Message",
        [
            {
                text: "Cancel",
                onPress: () => console.log("Cancel Pressed"),
                style: "cancel",
            },
            {
                text: "Submit",
                onPress: () => console.log("OK Pressed") ,
                style="cancel"
                },
        ],
        {
            cancelable: true
            onDismiss : () => {
                // code
            }
         }
    );
    ```

    -   **`title`** (String) : Le titre de l'alerte.

    -   **`message`** (String) Le message de l'alerte. Il apparaît sous le titre en texte régulier.

    -   **`buttons`** (Array) : Un tableau d'objets représentant les boutons de l'alerte. Chaque objet peut avoir les propriétés suivantes :

        -   **`text`** (String) : Le texte affiché sur le bouton.
        -   **`onPress`** (Function) : Une fonction callback appelée lorsque le bouton est pressé.
        -   **`style`** (String) : Le style du bouton. Les valeurs possibles sont `"default"`, `"cancel"`, et `"destructive"`. Le style `"cancel"` est souvent utilisé pour indiquer une action qui annule l'opération en cours.

    -   **`options`** (Object) :Un objet optionnel pour spécifier des paramètres supplémentaires pour l'alerte.

        -   **`cancelable`** (Boolean) : Indique si l'alerte peut être annulée en appuyant en dehors de la boîte de dialogue.
        -   **`onDismiss`** (Function) : Une fonction callback appelée lorsque l'alerte est annulée ou fermée sans appuyer sur aucun bouton.

-   **Exemple:**

    ```jsx
    import React from "react";
    import { View, Text, Button, Alert, StyleSheet } from "react-native";

    const App = () => {
        const showAlert = () => {
            Alert.alert(
                "Attention",
                "Voulez-vous vraiment continuer ?",
                [
                    {
                        text: "Annuler",
                        onPress: () => console.log("Annuler Pressé"),
                        style: "cancel",
                    },
                    { text: "OK", onPress: () => console.log("OK Pressé") },
                ],
                { cancelable: false }
            );
        };

        return (
            <View style={styles.container}>
                <Button title="Afficher une alerte" onPress={showAlert} />
            </View>
        );
    };

    const styles = StyleSheet.create({
        container: {
            flex: 1,
            justifyContent: "center",
            alignItems: "center",
        },
    });

    export default App;
    ```
