<template>
	<div class="flex items-center w-full border-b font-semibold py-3 uppercase last:border-none hover:text-red-600 cursor-pointer">
		{{ title }}
	</div>
</template>

<script setup>
defineProps({
	title: {
		type: String,
	},
});
</script>

<style lang="scss" scoped></style>
