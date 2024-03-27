<template>
	<div class="work-card-container">
		<div class="desc-container" @click="showDesc(true, false), (this.expanded = false)" @mouseenter="showDesc(false, true)" @mouseleave="showDesc(false, false)">
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
			<img
				ref="image"
				:src="require('../assets/' + img[this.index])"
				:class="{
					expanded: this.expanded,
					'wide-expanded': this.expandedWide && this.expanded,
					'tall-expanded': !this.expandedWide && this.expanded,
					rotate: this.expanded && this.expandedWide,
				}"
				@load="getImageSize"
			/>
			<div class="text-container" :style="this.expanded ? 'display: none' : 'display: flex'">
				<a :href="link"
					><div class="title">{{ title }}</div></a
				>
				<div class="type">{{ desc }}</div>
			</div>
			<LeftArrowIcon @click="changeImage(-1)" /><RightArrowIcon @click="changeImage(1)" /><CloseIcon @click="showDesc(true, false), expandImage(false)" /><ExpandIcon
				@click="expandImage"
				:expanded="this.expanded"
			/>
		</div>
	</div>
</template>

<script>
import LeftArrowIcon from "../components/svgs/LeftArrowIcon.vue";
import RightArrowIcon from "../components/svgs/RightArrowIcon.vue";
import CloseIcon from "../components/svgs/CloseIcon.vue";
import ExpandIcon from "../components/svgs/ExpandIcon.vue";

export default {
	props: ["title", "type", "desc", "img", "link"],
	components: { LeftArrowIcon, RightArrowIcon, CloseIcon, ExpandIcon },
	data() {
		return {
			descClicked: false,
			descHovered: false,
			expanded: false,
			expandedWide: false,
			index: 0,
			imageWidth: 0,
			imageHeight: 0,
		};
	},
	methods: {
		showDesc(clicked, hovered) {
			if (clicked) {
				this.descClicked = !this.descClicked;
				this.index = 0;
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
		expandImage() {
			this.expanded = !this.expanded;
		},
		getImageSize() {
			const img = this.$refs.image;
			this.imageWidth = img.naturalWidth;
			this.imageHeight = img.naturalHeight;

			if (this.imageWidth > this.imageHeight) {
				this.expandedWide = true;
			} else {
				this.expandedWide = false;
			}
		},
	},
};
</script>
