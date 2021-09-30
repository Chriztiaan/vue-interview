<template>
  <div class="hello">
    <div style="padding-bottom: 20px;">
      {{title}}
    </div>
    
    <div class="section">
      <button @click="updateTitle" :disabled="isButtonDisabled">Update title</button>
    </div>

    <div class="section">
      Let's show the count in a loop:
      <div v-for="i in 3" :key="i">
          method: {{ getCount() }}
      </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
export default Vue.extend({
  props: {
    title: {
      type: String,
      default: 'Empty'
    }
  },
  data() {
    return {
      count: 0,
      isButtonDisabled: false
    }
  },
  watch: {
    count() {
      if (this.count >= 5) {
        this.isButtonDisabled = true;
      }
      else {
        this.isButtonDisabled = false;
      }
    }
  },
  mounted() {
      if (this.count >= 5) {
        this.isButtonDisabled = true;
      }
      else {
        this.isButtonDisabled = false;
      }
  },
  methods: {
    updateTitle() {
      this.title = "New title";
      this.incrementCount();

      this.$emit('input', this.title);
      this.$emit('changed');
    },
    incrementCount() {
      this.count++;
    },
    getCount() {
      return this.count;
    }
  }
})
</script>

<style scoped>
button {
  background: lightcyan;
}

.section {
  padding-bottom: 20px;
}
</style>

<style >
button {
  font-size: 30px;
}
</style>


