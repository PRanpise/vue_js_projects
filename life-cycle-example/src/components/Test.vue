<template>
  <div>
    <p>I'm another component.</p>
    <p ref="dom-element">{{counter}}</p>
  </div>
</template>

<script>
export default {
  name: 'Test',
  data() {
    return {
      counter: 0,
    }
  },

  beforeUpdate() {
    console.log(this.counter) // Logs the counter value every second, before the DOM updates.
  },

  updated() {
    // Fired every second, should always be true
    console.log(+this.$refs['dom-element'].textContent === this.counter)
  },

  created() {
    setInterval(() => {
      this.counter++
    }, 1000)
  }
}
</script>