<template>
	<div class="work-card-container">
		<div class="desc-container" @click="showDesc(true, false)" @mouseenter="showDesc(false, true)" @mouseleave="showDesc(false, false)">
			<img :src="require('../assets/' + img)" />
			<div class="desc" :style="this.descClicked || this.descHovered ? 'opacity: 1' : 'opacity: 0'">{{ desc }}</div>
		</div>
		<div class="text-container">
			<div class="title">{{ title }}</div>
			<div class="type">{{ type }}</div>
		</div>
	</div>
</template>

<script>
export default {
	props: {
		title: String,
		type: String,
		desc: String,
		img: String,
		link: String,
	},
	data() {
		return {
			descClicked: false,
			descHovered: false,
		};
	},
	methods: {
		showDesc(clicked, hovered) {
			if (clicked) {
				this.descClicked = !this.descClicked;
			}
			this.descHovered = hovered;
		},
	},
};
</script>
