# cour 04 : **l'objet `route`:**

-   **Description:**

    > l'objet `route` contient des informations sur screen actuel et peut être utilisé pour accéder aux paramètres et autres détails de la route active.

-   **Propriétés de l'objet `route`:**

    1. **name** : `string`

        - Le nom de la route actuelle. Il est défini lors de la configuration des routes dans le navigateur.

    2. **key** : `string`

        - Une clé unique pour identifier cette route. Cette clé est générée automatiquement par React Navigation pour chaque instance de route.

    3. **params** : `object | undefined`
        - Un objet contenant les paramètres passés à cette route. Ces paramètres peuvent être utilisés pour transmettre des données entre différentes routes.

-   **Syntaxe:**

    ```js
    function Composnate({ route }) {
        const params = route.params;
        console.log(params);
    }
    ```

    -   il faut que `Composnate` soit deja ajouter dans `Stack.Screen` ie : ` <Stack.Screen name="nomDeScreen" component={Composnate} />`

    -   on peut utiliser le hook `useRoute` pour accerder à l'objet route : `const route = useRoute()`

-   **Exemple d'utilisation:**

    Pour illustrer l'utilisation de l'objet `route`, prenons un exemple où une application a deux écrans : `HomeScreen` et `DetailsScreen`. On veut naviguer de `HomeScreen` à `DetailsScreen` en passant des paramètres.

    -   **Configuration des routes:**

        ```javascript
        import * as React from "react";
        import { NavigationContainer } from "@react-navigation/native";
        import { createStackNavigator } from "@react-navigation/stack";
        import HomeScreen from "./HomeScreen";
        import DetailsScreen from "./DetailsScreen";

        const Stack = createStackNavigator();

        function App() {
            return (
                <NavigationContainer>
                    <Stack.Navigator initialRouteName="Home">
                        <Stack.Screen name="Home" component={HomeScreen} />
                        <Stack.Screen
                            name="Details"
                            component={DetailsScreen}
                        />
                    </Stack.Navigator>
                </NavigationContainer>
            );
        }

        export default App;
        ```

    -   **`HomeScreen` avec navigation vers `DetailsScreen`:**

        ```javascript
        import React from "react";
        import { Button, View, Text } from "react-native";

        function HomeScreen({ navigation }) {
            return (
                <View>
                    <Text>Home Screen</Text>
                    <Button
                        title="Go to Details"
                        onPress={() =>
                            navigation.navigate("Details", {
                                itemId: 86,
                                otherParam: "anything you want here",
                            })
                        }
                    />
                </View>
            );
        }

        export default HomeScreen;
        ```

    -   **`DetailsScreen` avec accès à l'objet `route`:**

        ```javascript
        import React from "react";
        import { View, Text } from "react-native";

        function DetailsScreen({ route, navigation }) {
            const { itemId, otherParam } = route.params;

            return (
                <View>
                    <Text>Details Screen</Text>
                    <Text>itemId: {itemId}</Text>
                    <Text>otherParam: {otherParam}</Text>
                </View>
            );
        }

        export default DetailsScreen;
        ```
