<script setup>
const props = defineProps(['tarefas']);
</script>

<template>
    <ul class="list-group">
    <li class="list-group-item d-flex align-items-center" v-for="tarefa in props.tarefas" :key="tarefa.titulo">
      <input class="form-check-input me-2" type="checkbox" @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada" :id="tarefa.titulo">
      <label :class="{ 'text-decoration-line-through': tarefa.finalizada }" class="mb-0 flex-grow-1" :for="tarefa.titulo">
        {{ tarefa.titulo }}
      </label>
    </li>
  </ul>
</template>
<style scoped>
.done{
  text-decoration: line-through;
}
</style>