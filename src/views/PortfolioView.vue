<template>
	<div class="portfolio-container">
		<div class="current-page">{{ $t("navBar." + route.name) }}</div>
		<hr class="nav-line" />
		<div class="type-container">
			<router-link :to="{ name: 'portfolio' }">{{ $t("portfolioView.skills.all") }}</router-link>
			<router-link :to="{ name: 'portfolio', params: { filter: 'web-design' } }">{{ $t("portfolioView.skills.webDesign") }}</router-link>
			<router-link :to="{ name: 'portfolio', params: { filter: 'graphic-design' } }">{{ $t("portfolioView.skills.graphicDesign") }}</router-link>
			<router-link :to="{ name: 'portfolio', params: { filter: '3d-design' } }">{{ $t("portfolioView.skills.design3D") }}</router-link>
			<router-link :to="{ name: 'portfolio', params: { filter: 'photography' } }">{{ $t("portfolioView.skills.photo") }}</router-link>
		</div>
		<hr class="line" />
		<div class="works-container">
			<WorkCard v-for="work in filterWorks(processedWorks)" :key="title" :title="work.title" :type="work.type" :desc="work.desc" :img="work.img" :link="work.link" />
		</div>
	</div>
</template>

<script>
import { useRoute } from "vue-router";

import WorkCard from "../components/WorkCard.vue";

export default {
	props: ["filter"],
	components: { WorkCard },
	computed: {
		route: () => useRoute(),
		processedWorks() {
			const works = [
				{
					title: this.$i18n.t("portfolioView.works.webDesign.work1.title"),
					type: this.$i18n.t("portfolioView.works.webDesign.type"),
					desc: this.$i18n.t("portfolioView.works.webDesign.work1.desc"),
					img: "placeholder.png",
					link: "",
					filter: "web-design",
				},
				{
					title: this.$i18n.t("portfolioView.works.design3D.work1.title"),
					type: this.$i18n.t("portfolioView.works.design3D.type"),
					desc: this.$i18n.t("portfolioView.works.design3D.work1.desc"),
					img: "placeholder.png",
					link: "",
					filter: "3d-design",
				},
				{
					title: this.$i18n.t("portfolioView.works.graphicDesign.work1.title"),
					type: this.$i18n.t("portfolioView.works.graphicDesign.type"),
					desc: this.$i18n.t("portfolioView.works.graphicDesign.work1.desc"),
					img: "placeholder.png",
					link: "",
					filter: "graphic-design",
				},
				{
					title: this.$i18n.t("portfolioView.works.photo.work1.title"),
					type: this.$i18n.t("portfolioView.works.photo.type"),
					desc: this.$i18n.t("portfolioView.works.photo.work1.desc"),
					img: "placeholder.png",
					link: "",
					filter: "photography",
				},
			];

			return works;
		},
	},
	methods: {
		filterWorks(processedWorks) {
			if (this.filter) {
				return this.processedWorks.filter((work) => work.filter == this.filter);
			} else {
				return processedWorks;
			}
		},
	},
};
</script>
