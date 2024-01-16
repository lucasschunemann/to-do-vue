<script setup>
    const props = defineProps(['cadastrarTarefa', 'tarefaTemp', 'trocarFiltro', 'editaTarefaTemp'])
</script>

<template>
    <form @submit.prevent="props.cadastrarTarefa" class="d-flex justify-content-between align-items-center mb-4">
      <div class="d-flex flex-grow-1 me-2">
        <input
          :value="props.tarefaTemp"
          @input="props.editaTarefaTemp"
          required
          type="text"
          placeholder="Nova tarefa..."
          class="form-control me-2"
        />
        <select @change="props.trocarFiltro" class="form-select">
          <option value="todas">Todas</option>
          <option value="pendentes">Pendentes</option>
          <option value="finalizadas">Finalizadas</option>
        </select>
      </div>
      <button type="submit" class="btn btn-success">Adicionar</button>
    </form>
  </template>