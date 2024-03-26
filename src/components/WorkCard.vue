<template>
	<div class="work-card-container">
		<div class="desc-container" @click="showDesc(true, false)" @mouseenter="showDesc(false, true)" @mouseleave="showDesc(false, false)">
			<img :src="require('../assets/' + img[0])" />
			<div class="desc" :style="this.descClicked || this.descHovered ? 'opacity: 1' : 'opacity: 0'">
				{{ desc }}
			</div>
		</div>
		<div class="text-container">
			<div class="title">{{ title }}</div>
			<div class="type">{{ type }}</div>
		</div>
		<div class="modal" :style="this.descClicked ? 'display: fixed' : 'display: none'">
			<img :src="require('../assets/' + img[this.index])" />
			<div class="text-container">
				<a :href="link"
					><div class="title">{{ title }}</div></a
				>
				<div class="type">{{ desc }}</div>
			</div>
			<LeftArrowIcon @click="changeImage(-1)" /><RightArrowIcon @click="changeImage(1)" /><CloseIcon @click="showDesc(true, false)" />
		</div>
	</div>
</template>

<script>
import LeftArrowIcon from "../components/svgs/LeftArrowIcon.vue";
import RightArrowIcon from "../components/svgs/RightArrowIcon.vue";
import CloseIcon from "../components/svgs/CloseIcon.vue";

export default {
	props: ["title", "type", "desc", "img", "link"],
	components: { LeftArrowIcon, RightArrowIcon, CloseIcon },
	data() {
		return {
			descClicked: false,
			descHovered: false,
			index: 0,
		};
	},
	methods: {
		showDesc(clicked, hovered) {
			if (clicked) {
				this.descClicked = !this.descClicked;
			}
			this.descHovered = hovered;
		},
		changeImage(dir) {
			this.index += dir;

			if (this.index < 0) {
				this.index = this.img.length - 1;
			} else if (this.index > this.img.length - 1) {
				this.index = 0;
			}
		},
	},
};
</script>
