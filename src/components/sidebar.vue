<template>
  <div class="sidebar">

      <p>Tarefas totais: {{TotalTasks}}</p>
      <p>Tarefas concluidas: {{CompletedTasks}}</p>
  </div>
</template>

<script>
export default {
  props: [
    "TotalTasks",
    "CompletedTasks"
  ]
}
</script>

<style>

</style>