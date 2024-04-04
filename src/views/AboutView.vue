<template>
	<div class="about-container">
		<div class="current-page-container">
			<div class="current-page">{{ $t("navBar." + route.name) }}</div>
			<hr class="nav-line" />
		</div>
		<div class="grid-container">
			<div class="grid-left-side">
				<div class="text-container">
					<div>
						{{ $t("aboutView.text1") }}
					</div>
					<br />
					<div>
						{{ $t("aboutView.text2") }}
					</div>
				</div>
			</div>
			<div class="grid-right-side">
				<div class="doing-container">
					<!-- <h1>{{ $t("aboutView.doing") }}</h1> -->
					<div class="card-container">
						<AboutCard v-for="card in processedCards" :key="card.type" :type="card.type" :desc="card.desc" :image="card.image">
							<component :is="card.image" />
						</AboutCard>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
import { useRoute } from "vue-router";

import AboutCard from "../components/AboutCard.vue";

import WebDevIcon from "../components/svgs/WebDevIcon.vue";
import WebDesignIcon from "../components/svgs/WebDesignIcon.vue";
import GraphicDesignIcon from "../components/svgs/GraphicDesignIcon.vue";
import Design3DIcon from "../components/svgs/Design3DIcon.vue";
import PhotoIcon from "../components/svgs/PhotoIcon.vue";

export default {
	name: "About",
	components: { AboutCard, WebDevIcon, WebDesignIcon, GraphicDesignIcon, Design3DIcon, PhotoIcon },
	computed: {
		route: () => useRoute(),
		processedCards() {
			const cards = [
				{ type: this.$i18n.t("aboutView.skills.webDev.title"), desc: this.$i18n.t("aboutView.skills.webDev.desc"), image: "WebDevIcon" },
				{ type: this.$i18n.t("aboutView.skills.webDesign.title"), desc: this.$i18n.t("aboutView.skills.webDesign.desc"), image: "WebDesignIcon" },
				{ type: this.$i18n.t("aboutView.skills.graphicDesign.title"), desc: this.$i18n.t("aboutView.skills.graphicDesign.desc"), image: "GraphicDesignIcon" },
				{ type: this.$i18n.t("aboutView.skills.design3D.title"), desc: this.$i18n.t("aboutView.skills.design3D.desc"), image: "Design3DIcon" },
				{ type: this.$i18n.t("aboutView.skills.photo.title"), desc: this.$i18n.t("aboutView.skills.photo.desc"), image: "PhotoIcon" },
			];

			return cards;
		},
	},
};
</script>
