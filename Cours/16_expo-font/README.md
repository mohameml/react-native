# cour 16 : **`expo-font`**

## 1. **expo-font:**

-   **Description:**

    > La méthode `expo-font` est une fonctionnalité fournie par le SDK d'Expo pour charger et utiliser des polices personnalisées dans une application React Native. Expo simplifie le processus de gestion des polices en offrant des API faciles à utiliser pour charger les polices avant que les composants de l'application ne soient rendus.

-   **Syntaxe:**

    -   **Installation:**

        ```bash
        npx expo install expo-font
        npx expo install expo-app-loading
        ```

    -   **Utilisation:**

        ```js
            import * as Font from "expo-font";
            import AppLoading from "expo-app-loading";

            const fetchFonts = () => {

                return Font.loadAsync({
                    'nom1':require("cheimn/vers/fihcier1.ttf")
                    'nom2':require("cheimn/vers/fihcier2.ttf")

                })
            }

            export default function App () {

                const [fetchData , setFecthData] = useState(true)

                if(fetchData) {
                    return (
                        <AppLoading
                            startAsync={fetchFonts}
                            onFinish={() => setFetchData(false)}
                            onError={(err) => console.log(err)}
                        />
                    )
                }


                return (
                    <Text style={{fontFamily : 'nom1'}}>Hello World<Text>
                )

            }
        ```

    -   **Exemple:**

        ```js
        import { useState } from "react";
        import { StyleSheet, View, ImageBackground, Text } from "react-native";
        import * as Font from "expo-font";

        const fetchFont = () => {
            return Font.loadAsync({
                pacifico: require("./assets/fonts/Pacifico-Regular.ttf"),
            });
        };

        export default function App() {
            const [fetchFonts, setFetchFonts] = useState(true);

            if (fetchFonts) {
                return (
                    <AppLoading
                        startAsync={fetchFont}
                        onFinish={() => setFetchFonts(false)}
                        onError={(err) => console.log(err)}
                    />
                );
            }

            return (
                <View style={styles.container}>
                    <Text style={{ fontFamily: "pacifico", fontSize: 30 }}>
                        Hello World
                    </Text>
                </View>
            );
        }

        const styles = StyleSheet.create({
            container: {
                padding: 20,
                paddingTop: 80,
                flex: 1,
                width: "100%",
                height: "100%",
            },
        });
        ```

    ![alt text](image.png)

## 2. **expo-google-font:**

-   **Description:**

    > La méthode `expo-google-fonts` est une fonctionnalité fournie par la bibliothèque expo-google-fonts, qui simplifie l'utilisation des polices Google Fonts dans une application React Native créée avec Expo. Cette bibliothèque permet de charger et d'utiliser facilement des polices Google sans avoir à les télécharger manuellement.

-   **Syntaxe:**

    -   **Installation:**

        ```bash
        npx expo install @expo-google-fonts/NomDeFonts

        ```

    -   **Utilisation:**

        ```js
        import {
            useFont,
            nomDeFontsDanslaDocs,
        } from "@expo-google-fonts/NomDeFonts";
        import AppLoading from "expo-app-loading";

        export default function App() {
            const [fontLoaded] = useFonts({
                nom1: nomDeFontsDanslaDocs,
                nom2 : require("chemin/vers/fichier.ttf"),
            });

            if (!fontLoaded) {
                return <AppLoading />;
            }

            return (
                // on return UI de notre App
                <Text style={{fontFamily : 'nom1'}}>Hello World<Text>
            )
        }
        ```

-   **Exemple:**

        ```js
        import { useState } from "react";
        import { StyleSheet, View, ImageBackground, Text } from "react-native";
        import * as Font from "expo-font";

        export default function App() {
            const [fontLoaded] = useFonts({
                    bg: Bangers_400Regular,
            });

            if (!fontLoaded) {
                return <AppLoading />;
            }

            return (
                <View style={styles.container}>
                    <Text style={{ fontFamily: "bg", fontSize: 30 }}>
                        Hello World
                    </Text>
                </View>
            );
        }

        const styles = StyleSheet.create({
            container: {
                padding: 20,
                paddingTop: 80,
                flex: 1,
                width: "100%",
                height: "100%",
            },
        });
        ```

![alt text](image-1.png)
