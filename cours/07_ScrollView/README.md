# cour 07 : **`ScrollView`**

-   **Description:**

    > `ScrollView` est un composant de React Native qui permet de créer des conteneurs scrollables pour afficher du contenu dépassant les dimensions de l'écran. C'est particulièrement utile lorsque vous avez besoin de présenter une grande quantité de contenu verticalement ou horizontalement.

-   **Syntaxe:**

    ```jsx
    import { ScrollView } from "react-native";

    <ScrollView>{/* Contenu à faire défiler */}</ScrollView>;
    ```

-   **Props Intéressantes du ScrollView:**

    -   **horizontal**: (boolean) Si true, le défilement se fait horizontalement au lieu de verticalement.
    -   **contentContainerStyle**: (object) Styles pour le conteneur de contenu.
    -   **showsVerticalScrollIndicator**: (boolean) Si false, cache l'indicateur de défilement vertical.
    -   **showsHorizontalScrollIndicator**: (boolean) Si false, cache l'indicateur de défilement horizontal.
    -   **onScroll**: (function) Fonction à appeler lorsque le contenu est défilé.
    -   **refreshControl**: (element) Composant pour ajouter une fonctionnalité de "pull to refresh".
    -   **pagingEnabled**: (boolean) Si true, le défilement se fait par pages, utile pour les carrousels.
    -   **scrollEventThrottle**: (number) Détermine la fréquence (en millisecondes) à laquelle l'événement de défilement est émis.

-   **Exemple:**

    ```jsx
    import { StatusBar } from "expo-status-bar";
    import { useState } from "react";
    import { Button, StyleSheet, Text, View, ScrollView } from "react-native";

    export default function App() {
        let infos = [
            {
                id: 1,
                name: "Ahmed",
                age: 25,
            },
            {
                id: 2,
                name: "Ahmed",
                age: 25,
            },
            {
                id: 3,
                name: "sidi",
                age: 20,
            },
            {
                id: 4,
                name: "Ahmed",
                age: 25,
            },
            {
                id: 5,
                name: "Ahmed",
                age: 25,
            },
            {
                id: 6,
                name: "Ahmed",
                age: 25,
            },
            {
                id: 7,
                name: "Ahmed",
                age: 25,
            },
            {
                id: 8,
                name: "Ahmed",
                age: 25,
            },
            {
                id: 9,
                name: "Ahmed",
                age: 25,
            },
        ];

        const infoList = infos.map((ele) => {
            return (
                <View style={styles.info} key={ele.id}>
                    <Text style={{ color: "white" }}>
                        my name is : {ele.name}
                    </Text>
                    <Text style={{ color: "white" }}>
                        {" "}
                        I am {ele.age} years old
                    </Text>
                </View>
            );
        });

        return (
            <ScrollView>
                <View style={styles.container}>
                    {/* <Text>Hello World</Text> */}
                    {infoList}
                </View>
            </ScrollView>
        );
    }

    const styles = StyleSheet.create({
        container: {
            // flex: 1,
            marginTop: 10,
            justifyContent: "center",
            alignItems: "center",
        },
        info: {
            width: "80%",
            padding: 20,
            borderRadius: 20,
            backgroundColor: "purple",
            marginBottom: 20,
        },
    });
    ```

    ![alt text](image.png)
