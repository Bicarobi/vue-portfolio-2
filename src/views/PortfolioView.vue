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
			<WorkCard v-for="work in filterWorks(processedWorks)" :key="work.title + work.type" :title="work.title" :type="work.type" :desc="work.desc" :img="work.img" :link="work.link" />
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
					img: ["web-design/work1/web-design-portfolio-old-1.jpeg", "web-design/work1/web-design-portfolio-old-2.jpeg"],
					link: "https://www.figma.com/proto/r67ggDZjAd5pDfe3gj3tdh/Portfolio-Dizajn?node-id=217-9&starting-point-node-id=217%3A9&scaling=scale-down-width&mode=design&t=QHplDNZBdXqlstwg-1",
					filter: "web-design",
				},
				{
					title: this.$i18n.t("portfolioView.works.webDesign.work2.title"),
					type: this.$i18n.t("portfolioView.works.webDesign.type"),
					desc: this.$i18n.t("portfolioView.works.webDesign.work2.desc"),
					img: ["web-design/work2/web-design-dont-waste-donate-1.jpeg", "web-design/work2/web-design-dont-waste-donate-2.jpeg"],
					link: "https://www.figma.com/proto/H15igXIS6OTLH5uDNd5QLd/don't-waste.-donate.?type=design&node-id=43-70&t=N2eKzCsgBaa9YaQC-1&scaling=min-zoom&page-id=1%3A3&starting-point-node-id=43%3A70&mode=design",
					filter: "web-design",
				},
				{
					title: this.$i18n.t("portfolioView.works.webDesign.work3.title"),
					type: this.$i18n.t("portfolioView.works.webDesign.type"),
					desc: this.$i18n.t("portfolioView.works.webDesign.work3.desc"),
					img: ["web-design/work3/web-design-wag-1.jpeg"],
					link: "https://www.figma.com/proto/AWytQoAax4V6SAdDQ7Y6U1/wag-landing-page?node-id=24-113&starting-point-node-id=24%3A113&mode=design&t=pf8cP3W0RVibYDi2-1",
					filter: "web-design",
				},
				{
					title: this.$i18n.t("portfolioView.works.design3D.work1.title"),
					type: this.$i18n.t("portfolioView.works.design3D.type"),
					desc: this.$i18n.t("portfolioView.works.design3D.work1.desc"),
					img: ["design-3d/work1/design-3d-bathroom.png"],
					link: "",
					filter: "3d-design",
				},
				{
					title: this.$i18n.t("portfolioView.works.design3D.work2.title"),
					type: this.$i18n.t("portfolioView.works.design3D.type"),
					desc: this.$i18n.t("portfolioView.works.design3D.work2.desc"),
					img: ["design-3d/work2/design-3d-bathroom2.jpg"],
					link: "",
					filter: "3d-design",
				},
				{
					title: this.$i18n.t("portfolioView.works.design3D.work3.title"),
					type: this.$i18n.t("portfolioView.works.design3D.type"),
					desc: this.$i18n.t("portfolioView.works.design3D.work3.desc"),
					img: [
						"design-3d/work3/design-3d-apartment-1.jpg",
						"design-3d/work3/design-3d-apartment-2.jpg",
						"design-3d/work3/design-3d-apartment-3.jpg",
						"design-3d/work3/design-3d-apartment-4.jpg",
						"design-3d/work3/design-3d-apartment-5.jpg",
						"design-3d/work3/design-3d-apartment-6.jpg",
						"design-3d/work3/design-3d-apartment-7.jpg",
						"design-3d/work3/design-3d-apartment-8.jpg",
						"design-3d/work3/design-3d-apartment-9.jpg",
						"design-3d/work3/design-3d-apartment-10.jpg",
						"design-3d/work3/design-3d-apartment-11.jpg",
					],
					link: "",
					filter: "3d-design",
				},
				{
					title: this.$i18n.t("portfolioView.works.appDesign.work1.title"),
					type: this.$i18n.t("portfolioView.works.appDesign.type"),
					desc: this.$i18n.t("portfolioView.works.appDesign.work1.desc"),
					img: ["app-design/work1/app-design-wag-1.jpeg", "app-design/work1/app-design-wag-2.jpeg"],
					link: "https://www.figma.com/file/paSSJxOVThrk3yc3A9DGKz/wag?type=design&node-id=0%3A1&mode=design&t=SSjheJrnJxQ9Cn5H-1",
					filter: "app-design",
				},
				{
					title: this.$i18n.t("portfolioView.works.appDesign.work2.title"),
					type: this.$i18n.t("portfolioView.works.appDesign.type"),
					desc: this.$i18n.t("portfolioView.works.appDesign.work2.desc"),
					img: [
						"app-design/work2/app-design-unin-setnja-1.jpeg",
						"app-design/work2/app-design-unin-setnja-2.png",
						"app-design/work2/app-design-unin-setnja-3.png",
						"app-design/work2/app-design-unin-setnja-4.png",
						"app-design/work2/app-design-unin-setnja-5.png",
					],
					link: "https://www.figma.com/proto/ayfe5znOiy90VDe1UOPu1O/UNIN-%C5%A0etnja-2.0?type=design&node-id=42-9&t=tKjxPb6nPsT9pY3t-1&scaling=scale-down&page-id=0%3A1&starting-point-node-id=42%3A9&show-proto-sidebar=1&mode=design",
					filter: "app-design",
				},
				{
					title: this.$i18n.t("portfolioView.works.appDesign.work3.title"),
					type: this.$i18n.t("portfolioView.works.appDesign.type"),
					desc: this.$i18n.t("portfolioView.works.appDesign.work3.desc"),
					img: [
						"app-design/work3/app-design-ecocompass-1.jpeg",
						"app-design/work3/app-design-ecocompass-2.png",
						"app-design/work3/app-design-ecocompass-3.png",
						"app-design/work3/app-design-ecocompass-4.png",
					],
					link: "https://www.figma.com/proto/pZVBU3tLHZRxUvpvkwuBBk/EcoCompass?type=design&node-id=172-544&t=0Lb399gH5R8Cn8zK-1&scaling=scale-down&page-id=0%3A1&starting-point-node-id=175%3A561&show-proto-sidebar=1&mode=design",
					filter: "app-design",
				},
				{
					title: this.$i18n.t("portfolioView.works.appDesign.work4.title"),
					type: this.$i18n.t("portfolioView.works.appDesign.type"),
					desc: this.$i18n.t("portfolioView.works.appDesign.work4.desc"),
					img: ["app-design/work4/app-design-cordova-ereader-1.png", "app-design/work4/app-design-cordova-ereader-2.png", "app-design/work4/app-design-cordova-ereader-3.png"],
					link: "https://www.figma.com/proto/pZVBU3tLHZRxUvpvkwuBBk/EcoCompass?type=design&node-id=172-544&t=0Lb399gH5R8Cn8zK-1&scaling=scale-down&page-id=0%3A1&starting-point-node-id=175%3A561&show-proto-sidebar=1&mode=design",
					filter: "app-design",
				},
				{
					title: this.$i18n.t("portfolioView.works.graphicDesign.work1.title"),
					type: this.$i18n.t("portfolioView.works.graphicDesign.type"),
					desc: this.$i18n.t("portfolioView.works.graphicDesign.work1.desc"),
					img: ["graphic-design/work1/graphic-design-zvirac.jpg"],
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
