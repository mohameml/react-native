# cour 03 : **L'objet `navigation` :**

-   **Description:**

    > L'objet `navigation` est un élément clé de React Navigation qui fournit des méthodes et des propriétés permettant de gérer la navigation dans une application React Native. Il est généralement passé automatiquement à chaque composant d'écran via les props par React Navigation.

-   **Syntaxe:**

    ```js
    function Composnate({ navigation }) {
        return <Button onPress={() => navigation.methode()} />;
    }
    ```

    -   il faut que `Composnate` soit deja ajouter dans `Stack.Screen` ie : ` <Stack.Screen name="nomDeScreen" component={Composnate} />`

    -   on peut utiliser le hook `useNavigation` pour accerder à l'objet navigation : `const navigation = useNavigation()`

-   **méthodes:**

| fonction                  | Syntaxe                                   | Description                                                                        |
| ------------------------- | ----------------------------------------- | ---------------------------------------------------------------------------------- |
| **`navigation.navigate`** | `navigation.navigate(screenName, params)` | permet de naviguer vers un écran spécifié                                          |
| **`navigation.push`**     | `navigation.push(screenName, params)`     | permet d'empiler un nouvel écran au sommet de la pile                              |
| **`navigation.goBack`**   | `navigation.goBack()`                     | revenir à l'écran précédent                                                        |
| **`navigation.replace`**  | `navigation.replace(screenName , params)` | retiré l'écran actuel de la pile de navigation et le remplacé par l'écran spécifié |
| **`navigation.popToTop`** | `navigation.popToTop()`                   | revenir directement à la première écran de la pile de navigation                   |
| **`navigation.pop`**      | `navigation.pop(count)`                   | retire un ou plusieurs écrans de la pile de navigation                             |

-   **Exemple:**

    ```javascript
    import * as React from "react";
    import { NavigationContainer } from "@react-navigation/native";
    import { createStackNavigator } from "@react-navigation/stack";
    import HomeScreen from "./screens/HomeScreen";
    import DetailsScreen from "./screens/DetailsScreen";

    const Stack = createStackNavigator();

    function App() {
        return (
            <NavigationContainer>
                <Stack.Navigator initialRouteName="Home">
                    <Stack.Screen name="Home" component={HomeScreen} />
                    <Stack.Screen name="Details" component={DetailsScreen} />
                </Stack.Navigator>
            </NavigationContainer>
        );
    }

    export default App;
    ```

    **HomeScreen.js**:

    ```javascript
    import React from "react";
    import { View, Text, Button } from "react-native";

    function HomeScreen({ navigation }) {
        return (
            <View>
                <Text>Home Screen</Text>
                <Button
                    title="Go to Details (navigate)"
                    onPress={() =>
                        navigation.navigate("Details", { itemId: 42 })
                    }
                />
                <Button
                    title="Go to Details (push)"
                    onPress={() => navigation.push("Details", { itemId: 42 })}
                />
            </View>
        );
    }

    export default HomeScreen;
    ```

    **DetailsScreen.js**:

    ```javascript
    import React from "react";
    import { View, Text, Button } from "react-native";

    function DetailsScreen({ route, navigation }) {
        // Retrieve the itemId parameter from route.params
        const { itemId } = route.params;

        return (
            <View>
                <Text>Details Screen</Text>
                <Text>Item ID: {itemId}</Text>
                <Button title="Go back" onPress={() => navigation.goBack()} />
                <Button
                    title="Go to Details again (push)"
                    onPress={() =>
                        navigation.push("Details", {
                            itemId: Math.floor(Math.random() * 100),
                        })
                    }
                />
                <Button
                    title="Go to Home"
                    onPress={() => navigation.navigate("Home")}
                />
            </View>
        );
    }

    export default DetailsScreen;
    ```
