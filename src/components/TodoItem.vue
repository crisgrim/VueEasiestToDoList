<template>
  <li :class="{'task--done': todo.done}">
    <p>{{ todo.id }}. {{ todo.text }}</p>
    <button @click="$emit('remove', todo.id)">
      <v-icon>highlight_off</v-icon>
    </button>
    <button 
      v-if="!todo.done"
      @click="$emit('markDone', todo.id)">
      <v-icon>done</v-icon>
    </button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../variables.scss";
p {
  color: $vue-second;
  display: inline-block;
  margin-right: 10px;
}
li {
  list-style: none;
}
.task--done {
  opacity: 0.5;
}
.task--done p {
  text-decoration: line-through;
}
</style>
