<template>
	<div
		v-if="show"
		class="translate-x-0 fixed z-10 bg-white dark:bg-darkGray-100 dark:text-white top-0 bottom-0 left-0 w-[600px] transform transition origin-right shadow-lg flex flex-col"
	>
		<slot />
	</div>
	<div
		v-if="show"
		className="inset-0 fixed z-0 bg-black opacity-50"
		@click="$emit('closeSideBar')"
	></div>
</template>

<script setup>
defineProps({
	show: {
		type: Boolean,
	},
});
defineEmits(["closeSideBar"]);
</script>

<style lang="scss" scoped></style>
