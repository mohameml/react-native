# cour 09

## 1. **`Image`:**

-   **Description:**

    > la composante `Image` est utilisée pour afficher des images. Elle supporte diverses sources d'images, telles que des images locales, des images provenant du réseau (internet), ou même des images encodées en base64.

-   **Syntaxe:**

    ```javascript
    import { Image } from "react-native";

    <Image source={require("path/to/image")} style={{resizeMode : valeur}} >

    ```

-   **Propriétés principales:**

    -   **`source`:** La propriété `source` spécifie la source de l'image.

    -   **`resizeMode`:** La propriété `resizeMode` contrôle comment l'image est redimensionnée pour s'adapter à ses dimensions. Les valeurs possibles incluent :

        -   `cover` : L'image est redimensionnée pour couvrir l'espace disponible en gardant son ratio d'aspect. Une partie de l'image peut être coupée.

        -   `contain` : L'image est redimensionnée pour être entièrement visible en gardant son ratio d'aspect. L'image peut être mise en boîte aux lettres.

        -   `stretch` : L'image est étirée pour remplir l'espace disponible, ce qui peut déformer l'image.

        -   `center` : L'image est centrée sans redimensionnement.

        -   `repeat` : L'image est répétée pour couvrir le cadre de la vue.

-   **Exemple:**

    ```javascript
    import React from "react";
    import { Image, StyleSheet, View } from "react-native";

    const App = () => {
        return (
            <View style={styles.container}>
                <Image
                    source={require("./path/to/local/image.png")}
                    style={styles.image}
                    resizeMode="cover"
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
        image: {
            width: 100,
            height: 50,
            resizeMode: "contain",
        },
    });

    export default App;
    ```

## 2. **`ImageBackground`:**

-   **Description:**

    > La composante `ImageBackground` de React Native permet d'afficher une image en arrière-plan d'un composant enfant. Elle fonctionne comme un conteneur, permettant de superposer d'autres composants (texte, boutons, etc.) sur une image de fond.

-   **Syntaxe:**

    ```javascript
    import { ImageBackground } from "react-native";
    <ImageBackground
        source={require("./path/to/local/image.jpg")}
        style={[styles.background, resizeMode : valeur]}
    >
        {/* Vos composants enfants ici */}
    </ImageBackground>;
    ```

-   **Exemple 1 :**

    ```javascript
    import { StatusBar } from "expo-status-bar";
    import { useState } from "react";
    import { StyleSheet, View, Text, ImageBackground } from "react-native";

    export default function App() {
        return (
            <View style={styles.container}>
                <ImageBackground source={require("OIP.jpeg")}>
                    <Text>Hello world !!</Text>
                </ImageBackground>
            </View>
        );
    }

    const styles = StyleSheet.create({
        container: {
            padding: 20,
            paddingTop: 50,
            backgroundColor: "#fff",
        },
    });
    ```

    ![alt text](image.png)

-   **Exemple 2 :**

    ```javascript
    import { View, ImageBackground, Text } from "react-native";
    import styles from "./style";
    import StyledButton from "../StyledButton/StyledButton";
    import { StyleSheet, Dimensions } from "react-native";

    export default function CardItem(props) {
        const { name, subtitle, tagLine, urlImage } = props;

        return (
            <View style={styles.cardContainer}>
                <ImageBackground source={urlImage} style={styles.image} />
                <View style={styles.infos}>
                    <Text style={styles.model}>{name}</Text>
                    <Text style={styles.price}>
                        {subtitle} <Text style={styles.tagLine}>{tagLine}</Text>
                    </Text>
                </View>
                <View style={styles.btns}>
                    <StyledButton
                        type="primary"
                        content="Custom Order"
                        onPress={() => console.log("Custom Order")}
                    />
                    <StyledButton
                        type="secondary"
                        content="Existing Inventory"
                        onPress={() => console.log("Existing Inventory")}
                    />
                </View>
            </View>
        );
    }



    const styles = StyleSheet.create({
        cardContainer: {
            width: "100%",
            height: Dimensions.get("window").height,
        },
        infos: {
            marginTop: "30%",
            width: "100%",
            alignItems: "center",
        },
        model: {
            fontSize: 40,
            fontWeight: "500",
        },
        price: {
            fontSize: 16,
            color: "#5c5e62",
        },
        image: {
            width: "100%",
            height: "100%",
            resizeMode: "cover",
            position: "absolute",
        },
        btns: {
            position: "absolute",
            bottom: 50,
            width: "100%",
        },
        tagLine: {
            textDecorationLine: "underline",
        },
    });

    export default styles;

    ```
