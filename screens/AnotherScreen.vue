<template>
    <touchable-opacity :on-press="handleButton" :style="{backgroundColor: 'red', padding: 10}">
      <text class="btn-text">Switch Screen back</text>
    </touchable-opacity>
</template>

<script>

export default {
  props: {
    navigation: {
      type: Object
    }
  },
  methods: {
    handleButton() {
      this.navigation.navigate("Home");
    },
  }
}
</script>