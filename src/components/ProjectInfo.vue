<script setup>
import { ref, onMounted } from 'vue'
import { marked } from 'marked'; // import the marked library

const props = defineProps({
	projectName: String
});

let data = ref(''); // define a reactive property

onMounted(async () => {
	const API_URL = `https://api.github.com/repos/${props.projectName}/contents/README.md`;
	const API_URL_2 = `https://api.github.com/repos/${props.projectName}/contents/README.MD`;
	try {
		const response = await fetch(API_URL);
		const jsonData = await response.json();
		const markdownContent = decodeURIComponent(escape(atob(jsonData.content)));
		data.value = marked(markdownContent); // convert the Markdown to HTML and assign it to data
	} catch (error) {
		console.error('Error fetching README.md:', error);
		try {
			const response2 = await fetch(API_URL_2);
			const jsonData2 = await response2.json();
			const markdownContent2 = decodeURIComponent(escape(atob(jsonData2.content)));
			data.value = marked(markdownContent2); // convert the Markdown to HTML and assign it to data
		} catch (error2) {
			console.error('Error fetching README.MD:', error2);
		}
	}
});
</script>

<template>
	<div class="py-5 container">
		<h1 class="text-success">Thông tin về {{ projectName }}</h1>
		<div style="padding: 0 20px;">
			<div v-if="data" v-html="data"></div>
			<div v-else>Loading...</div>
		</div>
	</div>
</template>

<style></style>
