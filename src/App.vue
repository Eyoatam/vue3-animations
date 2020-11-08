
<template>
	<router-view v-slot="slotProps">
		<transition name="fade-route" mode="out-in">
			<component :is="slotProps.Component"></component>
		</transition>
	</router-view>
	<!-- <div class="container">
		<div class="block" :class="{ animate: animatedBlock }"></div>
		<button @click="animateBlock">Animate</button>
	</div>
	<div class="container">
		<transition name="para" @before-enter="beforeEnter">
			<p v-if="paraVisible">This is only sometimes visible</p>
		</transition>
		<button @click="toggleParagraph">Toggle Paragraph</button>
	</div>
	<base-modal @close="hideDialog" :open="dialogIsVisible">
		<p>This is a test dialog!</p>
		<button @click="hideDialog">Close it!</button>
	</base-modal>
	<div class="container">
		<button @click="showDialog">Show Dialog</button>
	</div> -->
</template>  

<script>
export default {
	data() {
		return { dialogIsVisible: false, animatedBlock: false, paraVisible: false };
	},
	methods: {
		beforeEnter() {
			console.log('Before Enter');
		},
		animateBlock() {
			this.animatedBlock = !this.animatedBlock;
		},
		showDialog() {
			this.dialogIsVisible = true;
		},
		hideDialog() {
			this.dialogIsVisible = false;
		},
		toggleParagraph() {
			this.paraVisible = !this.paraVisible;
		},
	},
};
</script>

<style>
* {
	box-sizing: border-box;
}
html {
	font-family: sans-serif;
}
body {
	margin: 0;
}
button {
	font: inherit;
	padding: 0.5rem 2rem;
	border: 1px solid #810032;
	border-radius: 30px;
	background-color: #810032;
	color: white;
	cursor: pointer;
	outline: none;
}
button:hover,
button:active {
	background-color: #a80b48;
	border-color: #a80b48;
}
.block {
	width: 8rem;
	height: 8rem;
	background-color: #290033;
	margin-bottom: 2rem;
	transition: all 500ms ease-in-out;
}
.container {
	max-width: 40rem;
	margin: 2rem auto;
	display: flex;
	justify-content: center;
	align-items: center;
	flex-direction: column;
	padding: 2rem;
	border: 2px solid #ccc;
	border-radius: 12px;
}

.animate {
	animation: slide-fade 0.3s ease-out forwards;
}

.fade-route-enter-from,
.fade-route-leave-to {
	opacity: 0;
}

.fade-route-enter-active {
	transition: opacity 300ms ease-in-out;
}

.fade-route-leave-active {
	transition: opacity 300ms ease-out;
}

.fade-route-enter-to,
.fade-route-leave-from {
	opacity: 1;
}

.route-enter-active {
	animation: slide-fade 0.4s ease-in-out;
}

.route-leave-active {
	animation: slide-fade 0.4s ease reverse;
}

@keyframes slide-fade {
	0% {
		transform: translateX(0) scale(1);
	}
	70% {
		transform: translateX(-120px) scale(1.1);
	}
	100% {
		transform: translateX(-150px) scale(1);
	}
}
</style>
