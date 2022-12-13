<template>
	<div class="bg-red-600 py-1 px-2 text-sm text-white font-semibold">
		<span class=""> We are now shipping all across USA. ShopNow </span>
	</div>
	<div class="flex items-center justify-between w-full py-3 px-6 border-b">
		<div class="flex">
			<button class="flex xl:hidden items-center" @click="toggleSideBar">
				<vue-feather
					type="align-justify"
					strokeWidth="1"
					size="44"
					class="mr-2"
				/>
			</button>
			<img src="../assets/img/logo.png" class="w-20" />
			<div class="hidden xl:flex items-center ml-6">
				<div
					v-for="item in navbarItems"
					class="mr-3 uppercase font-bold hover:text-red-500 text-sm"
					:key="item"
				>
					{{ item }}
				</div>
			</div>
		</div>
		<div class="flex items-center">
			<div class="relative flex-1">
				<input
					class="border border-gray-300 px-2 py-1 w-full rounded-md"
					placeholder="Search"
				/>
				<vue-feather
					type="search"
					class="absolute top-1/2 right-1 -translate-y-1/2"
					size="16"
				/>
			</div>
			<div class="flex flex-col items-center mx-4 ml-8">
				<vue-feather type="user" />
				<div class="leading-none uppercase text-xs font-semibold mt-0.5">
					login
				</div>
			</div>
			<div class="flex flex-col items-center">
				<vue-feather type="shopping-bag" />
				<div class="leading-none uppercase text-xs font-semibold mt-0.5">
					cart
				</div>
			</div>
		</div>
	</div>
	<SideBar :show="showSideBar" @closeSideBar="toggleSideBar">
		<div
			class="w-full bg-red-600 py-4 px-6 text-white flex items-center justify-between"
		>
			<h1 class="uppercase font-semibold text-lg">Menu</h1>
			<button @click="toggleSideBar">
				<vue-feather type="x" />
			</button>
		</div>
		<div class="w-full px-6 flex-col flex mt-4">
			<NavbarItem v-for="item in navbarItems" :key="item" :title="item" />
		</div>
	</SideBar>
</template>

<script setup>
import { ref } from "vue";
import NavbarItem from "./NavbarItem.vue";
import SideBar from "./SideBar.vue";

let showSideBar = ref(false);
const toggleSideBar = () => (showSideBar.value = !showSideBar.value);

let navbarItems = [
	"new launch",
	"top wear",
	"bottom wear",
	"cosmetics",
	"footwear",
	"wishful",
	"plus sizes",
	"stories by w",
	"sale",
];
</script>

<style scoped></style>
