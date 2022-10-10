<script>
	import { RouterLink, RouterView } from 'vue-router';
	import Header from './components/Header.vue';
	import Posts from './components/Posts.vue';
	// const url = 'http://localhost:5002';
	const url = 'https://json-web-server.adaptable.app';
	export default {
		name: 'App',
		components: {
			Header,
			Posts,
		},
		data() {
			return {
				posts: [],
			};
		},
		async created() {
			this.posts = await this.getchBlogPosts();
			// this.posts = [
			// 	{
			// 		id: 1,
			// 		title: 'John',
			// 		description:
			// 			'lorem lorem lorem loremlorem loremlorem loremlorem loremlorem loremlorem loremlorem lorem',
			// 	},
			// 	{
			// 		id: 2,
			// 		title: 'John',
			// 		description:
			// 			'lorem lorem lorem loremlorem loremlorem loremlorem loremlorem loremlorem loremlorem lorem',
			// 	},
			// 	{
			// 		id: 3,
			// 		title: 'John',
			// 		description:
			// 			'lorem lorem lorem loremlorem loremlorem loremlorem loremlorem loremlorem loremlorem lorem',
			// 	},
			// 	{
			// 		id: 4,
			// 		title: 'John',
			// 		description:
			// 			'lorem lorem lorem loremlorem loremlorem loremlorem loremlorem loremlorem loremlorem lorem',
			// 	},
			// ];
		},
		methods: {
			async addBlogPost(blogPost) {
				const res = await fetch(`${url}/posts`, {
					method: 'POST',
					headers: {
						'Content-type': 'application/json',
					},
					body: JSON.stringify(blogPost),
				});
				const data = await res.json();
				this.posts = [...this.posts, data];
			},
			async getchBlogPosts() {
				const res = await fetch(`${url}/posts`);
				const data = await res.json();
				return data;
			},
			async getchBlogPost(id) {
				const res = await fetch(`${url}/posts/${id}`);
				const data = await res.json();
				return data;
			},
		},
	};
</script>

<template>
	<header class="border w-full flex flex-col items-center justify-center">
		<Header @add-blogPost="addBlogPost" />
		<Posts :posts="posts" />
		<!-- <RouterView /> -->
		<!-- <router-view></router-view> -->
	</header>
</template>
