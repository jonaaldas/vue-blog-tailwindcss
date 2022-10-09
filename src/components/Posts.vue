<template>
	<div class="flex flex-col items-center">
		<div
			class="w-3/5 rounded-3xl border border-indigo-400 p-3 m-3"
			v-for="(post, index) in posts"
			:key="index"
		>
			<h2 class="text-center font-bold">{{ post.title }}</h2>
			<div>
				<p class="text-xs">By: {{ post.author }}</p>
			</div>
			<p class="overflow-y-scrol">
				{{ post.description }}
			</p>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'Posts',
		props: {
			posts: {
				posts: Array,
			},
		},
		methods: {
			goTo(posts) {
				this.$emit('sending-posts', posts);
			},
		},
	};
</script>
