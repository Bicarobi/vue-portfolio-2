<template>
	<div class="profile-info-tag-container">
		<div class="grid-container">
			<div class="grid-left-side">
				<slot></slot>
			</div>
			<div class="grid-right-side">
				<div class="type">{{ type }}</div>
				<div class="description">{{ description }}</div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	props: ["type", "description"],
};
</script>
