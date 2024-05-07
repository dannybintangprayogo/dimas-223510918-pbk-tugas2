<template>
  <div>
    <h1>Welcome to My Vue Webpage</h1>
    <p>{{ message }}</p>
    <input type="text" v-model="inputText" @input="updateMessage">
    <p :class="{ 'red-text': isRed }" :style="{ fontSize: fontSize + 'px' }">{{ message }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: 'Initial message',
      inputText: '',
      isRed: false,
      fontSize: 16
    };
  },
  methods: {
    updateMessage() {
      this.message = this.inputText;
    },
    toggleColor() {
      this.isRed = !this.isRed;
    },
    increaseFontSize() {
      this.fontSize += 2;
    }
  },
  mounted() {
    // Add event listeners
    document.addEventListener('keypress', this.toggleColor);
    document.addEventListener('keydown', this.increaseFontSize);
  },
  destroyed() {
    // Remove event listeners to prevent memory leaks
    document.removeEventListener('keypress', this.toggleColor);
    document.removeEventListener('keydown', this.increaseFontSize);
  }
};
</script>

<style scoped>
.red-text {
  color: red;
}
</style>
