# Navigate between screens

In this chapter, we will implement navigation between screens in Contact app.

<p align="center">
  <img alt="Navigation between screens" src="introduction/final-product.gif">
</p>

The app will consist of 2 screens, home screen where it shows a list of contact and a contact details screen. By tapping the `ContactRow` in the Home screen, the app will navigate user to the contact details screen with the correct contact details.

# Step 1: Install dependencies

To implement navigation functionalities in the app, we need to install new dependencies.

```bash
npm install @react-navigation/native @react-navigation/native-stack
npx expo install react-native-screens react-native-safe-area-context
```

These dependencies are required for the app to use a library called [react-navigation](https://reactnavigation.org/docs/getting-started).

\*Make sure to restart Metro server to allow the app uses the installed dependencies.

# Step 2: Create a home screen

Starts by creating a native stack navigator

`createNativeStackNavigator` is a function that returns an object containing 2 properties: `Screen` and `Navigator`. Both of them are React components used for configuring the navigator. The `Navigator` should contain `Screen` elements as its children to define the configuration for routes.

`NavigationContainer` is a component which manages our navigation tree and contains the navigation state. This component must wrap all navigators structure. Usually, we’d render this component at the root of our app, which is usually the component exported from `App.tsx`.

```tsx
// App.tsx

import * as React from "react"
import { View, Text } from "react-native"
import { NavigationContainer } from "@react-navigation/native"
import { createNativeStackNavigator } from "@react-navigation/native-stack"

function HomeScreen() {
  return (
    <View style={{ flex: 1, alignItems: "center", justifyContent: "center" }}>
      <Text>Home Screen</Text>
    </View>
  )
}

const Stack = createNativeStackNavigator()

function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator>
        <Stack.Screen name="Home" component={HomeScreen} />
      </Stack.Navigator>
    </NavigationContainer>
  )
}

export default App
```
