<template>
	<div class="w-60 xl:w-96 max-h-min pt-6 pl-6 mr-4">
    <div class="px-3 py-3.5 uppercase font-bold border">filter</div>
		<div
			v-for="item in filters"
			:key="item"
			class="px-3 py-3.5 border border-t-0 capitalize flex items-center font-medium"
		>
			{{ item }}
		</div>
	</div>
</template>

<script setup>
const filters = [
	"category",
	"price",
	"discount",
	"color",
	"size",
	"neck type",
	"sleeve",
	"occasion",
	"length",
	"fastening/closure",
	"patter",
	"ornamentation",
	"fabric family",
	"closure",
];
</script>

<style lang="scss" scoped></style>
