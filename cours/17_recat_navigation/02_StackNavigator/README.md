# cour 02 : **Stack Navigation:`Native Stack`**

## 1. **Introduction:**

-   **Introduction:**

    > La **Stack Navigation** est un type de navigation couramment utilisé dans les applications mobiles, permettant de gérer une pile d'écrans où l'utilisateur peut naviguer en avant et en arrière. Chaque nouvel écran est empilé sur le précédent, et l'utilisateur peut revenir à l'écran précédent en "dépilant" les écrans un par un.

    -   Dans React Navigation, la Stack Navigation est implémentée à l'aide de `createStackNavigator` ou `createNativeStackNavigator`.

-   **Installation :**

    ```bash
    npm install @react-navigation/native-stack
    ```

-   **Configuration de la Navigation:** dans le fichier `App.js` :

    ```javascript
    import { NavigationContainer } from "@react-navigation/native";
    import { createStackNavigator } from "@react-navigation/stack";
    import Composnate from "./screens/Composnate";

    // creation de la stack Navigation :
    const Stack = createStackNavigator();

    function App() {
        return (
            <NavigationContainer>
                <Stack.Navigator>
                    <Stack.Screen name="nomDeScreen" component={Composnate} />
                    <Stack.Screen name="nom2" component={Composnate2} />
                </Stack.Navigator>
            </NavigationContainer>
        );
    }

    export default App;
    ```

## 2. **`Stack.Navigator` et `Stack.Screen`:**

-   **Description:**

    > **`Stack.Navigator`** et **`Stack.Screen`** sont deux composants clés utilisés pour configurer et gérer la navigation par pile dans une application React Native avec React Navigation.

    -   **`Stack.Navigator`**: Ce composant sert de conteneur principal pour définir la navigation par pile. Il encapsule et organise les différents écrans de l'application en une pile de navigation, permettant de passer de l'un à l'autre avec des transitions fluides.

    -   **`Stack.Screen`**: Ce composant représente chaque écran individuel au sein du `Stack.Navigator`. Il est utilisé pour spécifier les différents écrans qui composent la pile, ainsi que les paramètres et options spécifiques à chaque écran.

-   **Syntaxe:**

    -   **`Stack.Navigator`**:

        ```jsx
        <Stack.Navigator initialRouteName="Home">
            {/* Screens go here */}
        </Stack.Navigator>
        ```

        -   **`initialRouteName`** (optionnel) : Spécifie l'écran initial à afficher lorsque la pile de navigation est montée pour la première fois.

    -   **`Stack.Screen`**:

        ```jsx
        <Stack.Screen
            name="ScreenName"
            component={ScreenComponent}
            options={screenOptions}
        />
        ```

        -   **`name`** (obligatoire) : Le nom de l'écran, utilisé pour naviguer vers cet écran.
        -   **`component`** (obligatoire) : Le composant React représentant l'écran.
        -   **`options`** (optionnel) : Un objet ou une fonction qui retourne des options spécifiques pour l'écran, telles que le titre, les styles de header, etc.

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
                <Stack.Navigator>
                    <Stack.Screen name="Portfolio" component={Portfolio} />
                    <Stack.Screen name="Home" component={Home} />
                    <Stack.Screen name="Photo" component={Photo} />
                </Stack.Navigator>
            </NavigationContainer>
        );
    }

    export default App;
    ```

    <img src="./images/Home.jpg" width='500' height='800'/>

## 3. **L'objet `navigation` :**

-   **Description:**

    > L'objet `navigation` est un élément clé de React Navigation qui fournit des méthodes et des propriétés permettant de gérer la navigation dans une application React Native. Il est généralement passé automatiquement à chaque composant d'écran via les props par React Navigation.

-   **Syntaxe:**

    ```js
    function Composnate({ navigation }) {

        return(
            <Button
                onPress={() => navigation.methode()}
            >
        )
    }
    ```

    -   il faut que `Composnate` soit deja ajouter dans `Stack.Screen` ie : ` <Stack.Screen name="nomDeScreen" component={Composnate} />`

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
