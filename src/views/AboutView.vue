<template>
	<div class="about-container">
		<div class="current-page">{{ $t("nav." + route.name) }}</div>
		<hr class="nav-line" />

		<div class="text-container">
			<div>
				{{ $t("aboutView.text1") }}
			</div>
			<br />
			<div>
				Lorem ipsum dolor sit amet consectetur adipisicing elit. Hic recusandae unde numquam consequuntur dolores, neque doloremque voluptatem corporis cumque doloribus officiis delectus porro
				praesentium quos pariatur repellat ab tempora maxime iste deleniti quia esse architecto fuga? Ipsam, voluptatibus. Labore maiores quis quibusdam blanditiis ipsam provident quasi quidem
				aspernatur, quod ad perspiciatis dolorem autem iusto. A, vitae enim doloribus in inventore reprehenderit assumenda quisquam molestias adipisci debitis nemo est harum earum blanditiis
				at laboriosam. Sequi delectus repudiandae dolor qui totam error voluptate eaque consequuntur doloremque! Impedit, nobis earum eligendi unde neque rerum explicabo hic, cum tenetur totam
				aperiam vero. Adipisci, delectus?
			</div>
		</div>
		<div class="doing-container">
			<h1>{{ $t("aboutView.doing") }}</h1>
			<div class="card-container">
				<AboutCard v-for="card in processedCards" :key="card.type" :type="card.type" :desc="card.desc" :image="card.image">
					<component :is="card.image" />
				</AboutCard>
			</div>
		</div>
	</div>
</template>

<script>
import { useRoute } from "vue-router";

import AboutCard from "../components/AboutCard.vue";

import WebDevIcon from "../components/svgs/WebDevIcon.vue";
import WebDesignIcon from "../components/svgs/WebDesignIcon.vue";
import Design3DIcon from "../components/svgs/Design3DIcon.vue";
import PhotoIcon from "../components/svgs/PhotoIcon.vue";

export default {
	name: "About",
	components: { AboutCard, WebDevIcon, WebDesignIcon, Design3DIcon, PhotoIcon },
	computed: {
		route: () => useRoute(),
		processedCards() {
			const cards = [
				{ type: this.$i18n.t("aboutView.skills.web-dev.title"), desc: this.$i18n.t("aboutView.skills.web-dev.desc"), image: "WebDevIcon" },
				{ type: this.$i18n.t("aboutView.skills.web-design.title"), desc: this.$i18n.t("aboutView.skills.web-design.desc"), image: "WebDesignIcon" },
				{ type: this.$i18n.t("aboutView.skills.3d-design.title"), desc: this.$i18n.t("aboutView.skills.3d-design.desc"), image: "Design3DIcon" },
				{ type: this.$i18n.t("aboutView.skills.photo.title"), desc: this.$i18n.t("aboutView.skills.photo.desc"), image: "PhotoIcon" },
			];

			return cards;
		},
	},
};
</script>
