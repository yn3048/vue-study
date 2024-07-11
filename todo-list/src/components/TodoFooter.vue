<template>
    <div class="clearAllContainer">
        <span class="clearAllBtn" v-on:click="clearTodos">Clear All</span>
    </div>
</template>

<script>
export default {
  methods: {
    clearTodos(){
        this.$emit('removeAll');
    }
  },
}
</script>

<style scoped>
.clearAllContainer {
  width: 8.5rem;
  height: 50px;
  line-height: 50px;
  background-color: white;
  border-radius: 5px;
  margin: 20px auto;
}
.clearAllBtn {
  color: #ff2929;
  display: block;
  font-size: 18px;
  cursor: pointer;
}
</style>