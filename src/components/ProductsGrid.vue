<template>
	<div class="flex-1 h-full pt-6 overflow-scroll">
		<div v-if="siteData" class="border mr-6 flex items-center py-3 px-4 mx-2">
			<h1 class="mr-1">{{ count }}</h1>
			<div>items</div>
		</div>
		<div
			v-if="siteData"
			class="grid grid-cols-3 gap-6 xl:grid-cols-4 xl:gap-10 mt-4 px-2 pr-6"
			ref="scrollContainer"
		>
			<ProductCard
				v-for="item in siteData"
				:name="item.name"
				:img="item.image"
				:price="item.price"
				:variation="item.variation"
				:key="item.id_product"
			/>
		</div>
		<!-- <pre>{{ JSON.stringify(banner) }}</pre> -->
		<!-- <pre>{{ JSON.stringify(Object.keys(siteData.products[0]), null, 3) }}</pre> -->
	</div>
</template>

<script setup>
import axios from "axios";
import { onMounted, onUnmounted, ref, watchEffect } from "vue";
import ProductCard from "./ProductCard.vue";
const pageNumber = ref(1);
const siteData = ref([]);
const count = ref("");
const scrollContainer = ref(null);
watchEffect(async () => {
	try {
		const data = await axios.get(
			`https://pim.wforwoman.com/pim/pimresponse.php/?service=category&store=1&url_key=top-wear-kurtas&page=${pageNumber.value}&count=20&sort_by=&sort_dir=desc&filter=`
		);
		siteData.value.push(...data.data.result.products);
		count.value = data.data.result.count;
	} catch {}
});

onMounted(() => {
	window.addEventListener("scroll", handleScroll);
});

onUnmounted(() => {
	window.removeEventListener("scroll", handleScroll);
});

const handleScroll = (e) => {
	const element = scrollContainer.value;
	if (element.getBoundingClientRect().bottom < window.innerHeight) {
		pageNumber.value++;
	}
};
</script>

<style scoped></style>
