<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue'
import Formulario from './components/Formulario.vue'
import ListaTarefas from './components/ListaTarefas.vue'

  const estado = reactive({
    filtro: "todas",
    tarefaTemp: '',
    tarefas: [{
      titulo: 'Estudar ES6',
      finalizada: false,
    },
    {
      titulo: 'Estudar SASS',
      finalizada: false,
    },
    {
      titulo: 'Ir para academia',
      finalizada: true,
    }
    ]
  })

  const getNumeroPendentes = () => {
  return estado.tarefas.filter(tarefa => !tarefa.finalizada).length;
}

const getNumeroFinalizadas = () => {
  return estado.tarefas.filter(tarefa => tarefa.finalizada).length;
}

const getTarefasFiltradas = () => {
  const { filtro } = estado;
  switch (filtro) {
    case 'pendentes':
      return estado.tarefas.filter(tarefa => !tarefa.finalizada);
    case 'finalizadas':
      return estado.tarefas.filter(tarefa => tarefa.finalizada);
    default:
      return estado.tarefas;
  }
}

const cadastraTarefa = () => {
  const tarefaNova = {
    titulo: estado.tarefaTemp,
    finalizada: false,
  }
  estado.tarefas.push(tarefaNova);
  estado.tarefaTemp = '';
}
</script>

<template>
  <div class="app-background">
    <div class="container my-5 shadow-sm p-3 bg-white rounded" style="max-width: 600px;">
      <Cabecalho :tarefas-pendentes="getNumeroPendentes()"/>
      <Formulario 
        :cadastrarTarefa="cadastraTarefa" 
        :tarefaTemp="estado.tarefaTemp" 
        :editaTarefaTemp="evento => estado.tarefaTemp = evento.target.value" 
        :trocarFiltro="evento => estado.filtro = evento.target.value"
      />
      <ListaTarefas :tarefas="getTarefasFiltradas()"/>
    </div>
  </div>
</template>

<style scoped>
.app-background {
  background-color: #f8f9fa;
  min-height: 100vh;
  padding-top: 20px;
}

</style>

