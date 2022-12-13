<template>
	<div class="font-sans flex flex-col h-screen">
		<div class="fixed z-50 w-full bg-white shadow-lg">
			<Navbar />
		</div>
		<router-view class="mt-28 pb-5" v-slot="{ Component }">
			<component :is="Component" />
		</router-view>
	</div>
</template>
<script setup>
import { RouterLink, RouterView } from "vue-router";
import Navbar from "./components/Navbar.vue";
</script>
<style scoped></style>
