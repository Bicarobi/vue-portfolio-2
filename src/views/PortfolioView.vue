<template>
	<div class="portfolio-container">
		<div class="current-page-container">
			<div class="current-page">{{ $t("navBar." + route.name) }}</div>
			<hr class="nav-line" />
		</div>
		<div class="type-container">
			<router-link :to="{ name: 'portfolio' }">{{ $t("portfolioView.skills.all") }}</router-link>
			<router-link :to="{ name: 'portfolio', params: { filter: 'web-design' } }">{{ $t("portfolioView.skills.webDesign") }}</router-link>
			<router-link :to="{ name: 'portfolio', params: { filter: '3d-design' } }">{{ $t("portfolioView.skills.design3D") }}</router-link>
			<router-link :to="{ name: 'portfolio', params: { filter: 'app-design' } }">{{ $t("portfolioView.skills.appDesign") }}</router-link>
			<router-link :to="{ name: 'portfolio', params: { filter: 'graphic-design' } }">{{ $t("portfolioView.skills.graphicDesign") }}</router-link>
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
					img: ["web-design-portfolio-old.png", "placeholder.png"],
					link: "https://www.figma.com/proto/r67ggDZjAd5pDfe3gj3tdh/Portfolio-Dizajn?node-id=217-9&starting-point-node-id=217%3A9&scaling=scale-down-width&mode=design&t=QHplDNZBdXqlstwg-1",
					filter: "web-design",
				},
				{
					title: this.$i18n.t("portfolioView.works.webDesign.work2.title"),
					type: this.$i18n.t("portfolioView.works.webDesign.type"),
					desc: this.$i18n.t("portfolioView.works.webDesign.work2.desc"),
					img: ["web-design-dont-waste-donate.png"],
					link: "https://www.figma.com/proto/H15igXIS6OTLH5uDNd5QLd/don't-waste.-donate.?type=design&node-id=43-70&t=N2eKzCsgBaa9YaQC-1&scaling=min-zoom&page-id=1%3A3&starting-point-node-id=43%3A70&mode=design",
					filter: "web-design",
				},
				{
					title: this.$i18n.t("portfolioView.works.design3D.work1.title"),
					type: this.$i18n.t("portfolioView.works.design3D.type"),
					desc: this.$i18n.t("portfolioView.works.design3D.work1.desc"),
					img: ["design-3d-bathroom.png"],
					link: "",
					filter: "3d-design",
				},
				{
					title: this.$i18n.t("portfolioView.works.design3D.work1.title"),
					type: this.$i18n.t("portfolioView.works.design3D.type"),
					desc: this.$i18n.t("portfolioView.works.design3D.work1.desc"),
					img: ["design-3d-bathroom2.jpg"],
					link: "",
					filter: "3d-design",
				},
				{
					title: this.$i18n.t("portfolioView.works.appDesign.work1.title"),
					type: this.$i18n.t("portfolioView.works.appDesign.type"),
					desc: this.$i18n.t("portfolioView.works.appDesign.work1.desc"),
					img: ["app-design-wag.png"],
					link: "https://www.figma.com/file/paSSJxOVThrk3yc3A9DGKz/wag?type=design&node-id=0%3A1&mode=design&t=SSjheJrnJxQ9Cn5H-1",
					filter: "app-design",
				},
				{
					title: this.$i18n.t("portfolioView.works.appDesign.work2.title"),
					type: this.$i18n.t("portfolioView.works.appDesign.type"),
					desc: this.$i18n.t("portfolioView.works.appDesign.work2.desc"),
					img: ["app-design-unin-setnja.png"],
					link: "https://www.figma.com/proto/ayfe5znOiy90VDe1UOPu1O/UNIN-%C5%A0etnja-2.0?type=design&node-id=42-9&t=tKjxPb6nPsT9pY3t-1&scaling=scale-down&page-id=0%3A1&starting-point-node-id=42%3A9&show-proto-sidebar=1&mode=design",
					filter: "app-design",
				},
				{
					title: this.$i18n.t("portfolioView.works.appDesign.work3.title"),
					type: this.$i18n.t("portfolioView.works.appDesign.type"),
					desc: this.$i18n.t("portfolioView.works.appDesign.work3.desc"),
					img: ["app-design-ecocompass.png"],
					link: "https://www.figma.com/proto/pZVBU3tLHZRxUvpvkwuBBk/EcoCompass?type=design&node-id=172-544&t=0Lb399gH5R8Cn8zK-1&scaling=scale-down&page-id=0%3A1&starting-point-node-id=175%3A561&show-proto-sidebar=1&mode=design",
					filter: "app-design",
				},
				{
					title: this.$i18n.t("portfolioView.works.appDesign.work4.title"),
					type: this.$i18n.t("portfolioView.works.appDesign.type"),
					desc: this.$i18n.t("portfolioView.works.appDesign.work4.desc"),
					img: ["app-design-cordova-ereader.png"],
					link: "https://www.figma.com/proto/pZVBU3tLHZRxUvpvkwuBBk/EcoCompass?type=design&node-id=172-544&t=0Lb399gH5R8Cn8zK-1&scaling=scale-down&page-id=0%3A1&starting-point-node-id=175%3A561&show-proto-sidebar=1&mode=design",
					filter: "app-design",
				},
				{
					title: this.$i18n.t("portfolioView.works.graphicDesign.work1.title"),
					type: this.$i18n.t("portfolioView.works.graphicDesign.type"),
					desc: this.$i18n.t("portfolioView.works.graphicDesign.work1.desc"),
					img: ["graphic-design-zvirac.jpg"],
					link: "",
					filter: "graphic-design",
				},
				{
					title: this.$i18n.t("portfolioView.works.photo.work1.title"),
					type: this.$i18n.t("portfolioView.works.photo.type"),
					desc: this.$i18n.t("portfolioView.works.photo.work1.desc"),
					img: ["placeholder.png"],
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
