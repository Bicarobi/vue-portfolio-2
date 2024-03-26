<template>
	<div class="work-card-container">
		<div class="desc-container" @click="showDesc(true, false)" @mouseenter="showDesc(false, true)" @mouseleave="showDesc(false, false)">
			<img :src="require('../assets/' + img[img.length - 1])" />
			<div class="desc" :style="this.descClicked || this.descHovered ? 'opacity: 1' : 'opacity: 0'">
				{{ desc }}
			</div>
		</div>
		<div class="text-container">
			<div class="title">{{ title }}</div>
			<div class="type">{{ type }}</div>
		</div>
		<div class="modal" @click="showDesc(true, false)" :style="this.descClicked ? 'display: fixed' : 'display: none'">
			<img :src="require('../assets/' + img[img.length - 1])" />
			<div class="text-container">
				<a :href="link"
					><div class="title">{{ title }}</div></a
				>
				<div class="type">{{ desc }}</div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	props: ["title", "type", "desc", "img", "link"],
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
