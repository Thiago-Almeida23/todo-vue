<script setup>
import { mergeProps } from 'vue';

    const props = defineProps(['tarefas']);
</script>

<template>
    <div>
      <ul class="list-group mt-4" v-if="props.tarefas.length > 0">
        <li class="list-group-item" v-for="tarefa in props.tarefas" :key="tarefa.titulo">
          <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada" :id="tarefa.titulo" type="checkbox">
          <label :class="{ done: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">{{ tarefa.titulo }}</label>
        </li>
      </ul>
      <p v-else class="message">Não existem tarefas pendentes.</p>
    </div>
  </template>

<style scoped>
    .done {
        text-decoration: line-through;
    }

    .message {
  margin-top: 30px; 
}
</style>