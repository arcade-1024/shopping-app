<template>
	<div
		class="flex flex-col items-center h-full"
		@mouseenter="mouseEnter"
		@mouseleave="mouseleave"
	>
		<div class="relative overflow-hidden w-full">
			<img :src="img" class="w-full" alt="" />
			<Transition name="banner">
				<div
					v-if="banner"
					class="absolute bg-red-700 py-2 w-full bottom-0 px-3 text-white text-center uppercase text-sm"
				>
					view details
				</div>
			</Transition>
		</div>
		<div :class="banner ? 'w-full border box-content border-t-0' : 'w-full'">
			<div class="w-full px-2 pb-2">
				<h1 class="mt-2 w-full text-sm flex-wrap">
					{{ name }}
				</h1>
				<p class="mt-1 font-semibold">Rs. {{ price }}</p>
				<div class="h-14 mt-1.5">
					<Transition name="variation">
						<div v-if="banner" class="flex items-center flex-wrap">
							<span class="mr-2 text-sm">sizes - </span>
							<div
								class="w-6 h-6 flex items-center justify-center rounded-full hover:bg-red-400 text-sm hover:text-white mr-2 mt-1 cursor-pointer transition"
								v-for="item in Object.keys(variation)"
								:key="item"
							>
								{{ item }}
							</div>
						</div>
					</Transition>
				</div>
			</div>
		</div>
	</div>
</template>

<script setup>
import { ref } from "vue";
defineProps({
	img: {
		type: String,
	},
	variation: {
		type: Object,
	},
	name: {
		type: String,
	},
	price: {
		type: String,
	},
});
const banner = ref(false);
const mouseEnter = () => (banner.value = true);
const mouseleave = () => (banner.value = false);
</script>

<style scoped>
.banner-enter-active,
.banner-leave-active {
	transition: all 0.4s cubic-bezier(1, 0.5, 0.8, 1);
}
.banner-enter-from {
	opacity: 0;
	transform: translate(0, 50px);
}
.banner-leave-to {
	opacity: 0;
	transform: translate(0, 50px);
}

.variation-leave-active,
.variation-enter-active {
	transition: opacity 0.4s ease;
}
.variation-enter-from,
.variation-leave-to {
	opacity: 0;
}
</style>
