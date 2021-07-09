<template>
	<li>
		<span>{{tarea.text}}</span>
		<button @click.prevent="$emit('del', tarea)">Eliminar</button>
	</li>
</template>

<script setup>
import { defineProps } from 'vue'

defineProps({
  tarea: Object
});

</script>

<style scoped>
li {
  margin: 5px 0;
	padding: 0px;
	display: flex;
}

span {
	flex: 1;
}

button {
	border: 1px solid orangered;
	background-color: brown;
	color: white;
	font-size: 0.8rem;
	padding: 2px 4px;
}
button:hover {
	border-color: orange ;
	background-color: #ff8100;
}

</style>