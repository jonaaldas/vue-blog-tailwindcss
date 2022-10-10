<script>
	export default {
		name: 'Header',
		data() {
			return {
				title: '',
				description: '',
			};
		},
		methods: {
			onSubmit(e) {
				e.preventDefault();
				const newBlog = {
					title: this.title,
					description: this.description,
				};
				this.$emit('add-blogPost', newBlog);
				this.title = '';
				this.description = '';
			},
		},
	};
</script>
<template>
	<header class="contianer flex flex-col items-center w-3/4">
		<h1 class="text-4xl text-center">Jonathan's Blog</h1>
		<h3 class="text-2xl text-center text-cyan-900">
			Things I Love To Talk About!
		</h3>
		<form
			@submit="onSubmit"
			class="flex flex-col w-2/4 items-center mb-2"
		>
			<label for="title">Title</label>
			<input
				type="text"
				name="title"
				v-model="title"
				class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500"
			/>
			<label for="description">Descritpion</label>
			<textarea
				name="description"
				cols="30"
				rows="10"
				v-model="description"
				class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500"
			></textarea>
		</form>

		<button
			@click="onSubmit"
			type="submit"
			class="focus:outline-none text-white bg-purple-700 hover:bg-purple-800 focus:ring-4 focus:ring-purple-300 font-medium rounded-lg text-sm px-5 py-2.5 mb-2"
		>
			Add Blog Post
		</button>
	</header>
</template>
