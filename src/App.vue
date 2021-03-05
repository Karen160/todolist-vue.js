
<template>
  <div id="app">
     <section class="hero is-warning is-bold is-fullheight">
       <TodoCard/>
    </section>
    </div>
</template>

<script>
import TodoCard from './components/TodoCard.vue'

export default {
  
  name: 'app',
  components: {
    TodoCard
  },
}
</script>

<style>

</style>