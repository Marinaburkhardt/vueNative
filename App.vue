<template>
  <app-navigator></app-navigator>
</template>

<script>
import {
  createAppContainer,
  createStackNavigator,
} from "vue-native-router";

import HomeScreen from "./screens/HomeScreen.vue";
import AnotherScreen from "./screens/AnotherScreen.vue";

const StackNavigator = createStackNavigator(
  {
    Home: HomeScreen,
    Another: AnotherScreen
  },
  {
    initialRouteName: 'Home',
  }
);

const AppNavigator = createAppContainer(StackNavigator);

export default {
  components: { AppNavigator },
}
</script>