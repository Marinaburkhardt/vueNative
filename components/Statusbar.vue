<template>
  <SafeAreaView forceInset={{bottom: 'never'}}>
    <view class="statusbar" :style="{ backgroundColor: color }"></view>
  </SafeAreaView>
</template>

<script>
import { SafeAreaView } from 'react-native-safe-area-view';
export default {
  props: ['color']
}
</script>

<style>
.statusbar {
  height: 20px;
}
</style>