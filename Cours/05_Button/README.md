# cour 05 : **Button**

-   **Description:**

    > Le composant `Button` de React Native est un composant simple pour afficher un bouton cliquable. Il est facile à utiliser et rapide à mettre en place pour des actions basiques comme soumettre des formulaires ou déclencher des événements.

-   **Syntaxe:**

    ```jsx
    import { Button } from "react-native";

    <Button
        onPress={() => {
            /* action à exécuter */
        }}
        title="Cliquez-moi"
    />;
    ```

    -   Pour utiliser le composant `Button`, vous devez l'importer depuis `react-native`.

-   **Props Intéressantes du Button:**

    -   **title**: (string) Texte à afficher sur le bouton.
    -   **onPress**: (function) Fonction à exécuter lorsque le bouton est pressé.
    -   **color**: (string) Couleur du texte du bouton. Par défaut, il utilise la couleur par défaut du système.
    -   **disabled**: (boolean) Si true, le bouton sera désactivé et non cliquable.

-   **Exemple:**

    ```jsx
    import React from "react";
    import { View, Button, Alert, StyleSheet } from "react-native";

    const App = () => {
        const handlePress = () => {
            Alert.alert("Bouton Pressé", "Vous avez pressé le bouton !");
        };

        return (
            <View style={styles.container}>
                <Button
                    onPress={handlePress}
                    title="Cliquez-moi"
                    color="#841584"
                />
                <Button
                    onPress={() => {}}
                    title="Bouton Désactivé"
                    color="#841584"
                    disabled={true}
                />
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
