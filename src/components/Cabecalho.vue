<script setup>
    const props = defineProps(['tarefasPendentes'])
</script>

<template>
    <header class="text-center my-4">
        <h1 class="display-5 fw-bold">Minhas Tarefas</h1>
        <p class="text-muted">
            {{ props.tarefasPendentes }} tarefas pendentes
        </p>
    </header>
</template>