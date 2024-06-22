# cour 05 :

## 1. **options `header`:**

-   **Description:**

    > Dans React Navigation, le composant `header` est une partie essentielle de la barre de navigation supérieure. Il permet de personnaliser l'apparence et le comportement de l'en-tête de vos écrans.

    -   Le `header` est utilisé pour afficher des informations ou des actions en haut de l'écran. Il peut inclure des éléments tels que le titre de l'écran, des boutons de navigation, des icônes, etc. Vous pouvez personnaliser son apparence et son comportement en utilisant diverses options fournies par React Navigation.

-   **Propriétés du `header`:**

    -   **title**: Le titre de l'écran affiché dans le header.
    -   **headerTitle:** définir le composante affiché dans l'en-tête (header) d'un écran
    -   **headerStyle**: Style de la vue du header.
    -   **headerTintColor**: Couleur du texte et des icônes dans le header.
    -   **headerTitleStyle**: Style du texte du titre du header.
    -   **headerRight**: Composant personnalisé à afficher à droite du header.
    -   **headerLeft**: Composant personnalisé à afficher à gauche du header.
    -   **headerShown**: Booléen pour afficher ou masquer le header.
    -   **headerBackTitle**: Titre du bouton de retour.
    -   **headerTransparent**: Booléen pour rendre le header transparent.

-   **Syntaxe :**

    ```js
    <Stack.Navigator
        options={{
            title :"Title",
            headerTitle : () => {
                // composnate for title
            }
            headerStyle: {
                backgroundColor: "#f4511e",
            },
            headerTintColor: "#fff",
            headerTitleStyle: {
                fontWeight: "bold",
            },
        }}
    />
    ```

-   **Exemple :**

    ```javascript
    import React from "react";
    import { NavigationContainer } from "@react-navigation/native";
    import { createStackNavigator } from "@react-navigation/stack";
    import HomeScreen from "./HomeScreen";
    import DetailsScreen from "./DetailsScreen";

    const Stack = createStackNavigator();

    function App() {
        return (
            <NavigationContainer>
                <Stack.Navigator
                    screenOptions={{
                        headerStyle: {
                            backgroundColor: "#f4511e",
                        },
                        headerTintColor: "#fff",
                        headerTitleStyle: {
                            fontWeight: "bold",
                        },
                    }}
                >
                    <Stack.Screen
                        name="Home"
                        component={HomeScreen}
                        options={{ title: "Accueil" }}
                    />
                    <Stack.Screen
                        name="Details"
                        component={DetailsScreen}
                        options={{
                            title: "Détails",
                            headerRight: () => (
                                <Button
                                    onPress={() => alert("This is a button!")}
                                    title="Info"
                                    color="#fff"
                                />
                            ),
                        }}
                    />
                </Stack.Navigator>
            </NavigationContainer>
        );
    }

    export default App;
    ```

## 2. **`options` , `screenOptions` ,`setOptions`:**

-   **Description:**

    > Dans React Navigation, il existe plusieurs façons de styliser le `header` d'un écran. Vous pouvez utiliser les options du composant `Stack.Screen`, les `screenOptions` du composant `Stack.Navigator`, ou la méthode `setOptions` dans le composant de l'écran lui-même. Chacune de ces approches offre une flexibilité différente en termes de où et comment vous appliquez les styles.

    -   Vous pouvez définir des options par défaut pour tous les écrans d'un `Stack.Navigator` en utilisant la propriété `screenOptions`.

    -   Vous pouvez également définir les options du `header` à l'intérieur du composant de l'écran en utilisant la méthode `setOptions`.

    -   La priorité des méthodes est la suivante : `setOptions` , `options` puis `screenOptions`.

-   **Syntaxe:**

    ```javascript
    // **Utiliser les options du `Stack.Screen`:**
    <Stack.Screen
        name="ScreenName"
        component={ScreenComponent}
        options={{
            headerStyle: { backgroundColor: "#f4511e" },
            headerTintColor: "#fff",
            headerTitleStyle: { fontWeight: "bold" },
        }}
        // ou
        options={({navigation , route}) => {

            return {
                headerStyle: { backgroundColor:route.params.fvcolor},
                headerTintColor: "#fff",
                headerTitleStyle: { fontWeight: "bold" },
            }
        }}
    />

    //Utiliser `screenOptions` du `Stack.Navigator`
    <Stack.Navigator
        screenOptions={{
            headerStyle: { backgroundColor: "#f4511e" },
            headerTintColor: "#fff",
            headerTitleStyle: { fontWeight: "bold" },
        }}
    >
        <Stack.Screen name="ScreenName" component={ScreenComponent} />
        <Stack.Screen name="AnotherScreenName" component={AnotherScreenComponent} />
    </Stack.Navigator>

    // Utiliser `setOptions` dans le composant de l'écran lui-même
    function ScreenComponent({ navigation }) {

    useLayoutEffect(() => {
        navigation.setOptions({
        title: 'New Title',
        headerStyle: { backgroundColor: '#f4511e' },
        headerTintColor: '#fff',
        });
    }, [navigation]);

    return (
        // Votre composant
    );
    }
    ```
