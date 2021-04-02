<template>
	<FaqCard />
</template>

<script>
	import FaqCard from './components/FaqCard.vue';
	export default {
		components: {
			FaqCard,
		},
	};

	// This starter template is using Vue 3 experimental <script setup> SFCs
	// Check out https://github.com/vuejs/rfcs/blob/script-setup-2/active-rfcs/0000-script-setup.md
</script>
<style lang="scss">
	body {
		background: linear-gradient(
				$bg-gradient-soft-violet 60%,
				$bg-gradient-soft-blue
			)
			no-repeat;
		display: flex;
		justify-content: center;
		align-items: center;
		min-height: 100vh;

		@media screen and (min-width: $desktop) {
			background: linear-gradient(
				$bg-gradient-soft-violet 10%,
				$bg-gradient-soft-blue
			);
		}
	}
</style>
