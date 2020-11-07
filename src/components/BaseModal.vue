<template>
	<div v-if="open" class="backdrop" @click="$emit('close')"></div>
	<transition name="dialog">
		<dialog open v-if="open">
			<slot></slot>
		</dialog>
	</transition>
</template>

<script>
export default {
	props: ['open'],
	emits: ['close'],
};
</script>

<style scoped>
.backdrop {
	position: fixed;
	top: 0;
	left: 0;
	width: 100%;
	height: 100vh;
	z-index: 10;
	background-color: rgba(0, 0, 0, 0.5);
}

dialog {
	position: fixed;
	top: 30vh;
	width: 30rem;
	left: calc(50% - 15rem);
	margin: 0;
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
	border-radius: 12px;
	padding: 1rem;
	background-color: white;
	z-index: 100;
	border: none;
	/* animation: modal 0.5s ease-in-out forwards; */
}
.dialog-enter-active {
	animation: modal 0.3s ease-in-out;
}

.dialog-leave-active {
	animation: modal 0.2s ease-out reverse;
}

@keyframes modal {
	from {
		opacity: 0;
		transform: translateY(-150px);
	}
	/* 50% {
		transform: translateY(-150px);
	} */
	to {
		opacity: 1;
		transform: translateY(0);
	}
}
</style>