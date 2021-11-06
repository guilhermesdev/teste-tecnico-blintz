<template>
	<section>
		<div
			v-for="realState in realStateList"
			:key="realState.address + realState.image"
			class="card"
		>
			{{ realState.address }}
		</div>
	</section>
</template>

<script>
import realStateList from '@/data/realState';

export default {
	name: 'RealStateList',
	data() {
		return {
			realStateList
		}
	}
}
</script>

<style lang="scss" scoped>
.card {
	display: flex;
  justify-content: space-between;
  align-items: center;

  background-color: var(--color-bg-header);
  padding: 2rem 1.5rem;

  border-radius: .3rem;
  border: 2px solid var(--color-border);

	&:not(:last-child) {
		margin-bottom: .7rem;
	}
}
</style>