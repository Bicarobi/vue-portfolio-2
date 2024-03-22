<template>
	<div class="resume-container">
		<div class="current-page">{{ $t("navBar." + route.name) }}</div>
		<hr class="nav-line" />
		<div class="content-container">
			<div class="type-container">
				<EducationIcon />
				<h1>{{ $t("resumeView.education") }}</h1>
			</div>
			<div style="padding-left: 55px">
				<ResumeInfo v-for="info in processedEduInfo" :key="title" :title="info.title" :time="info.time" :desc="info.desc" />
			</div>
		</div>
		<hr class="line" />
		<div class="content-container">
			<div class="type-container">
				<WorkIcon />
				<h1>{{ $t("resumeView.experience") }}</h1>
			</div>
			<div style="padding-left: 55px">
				<ResumeInfo v-for="info in processedWorkInfo" :key="title" :title="info.title" :time="info.time" :desc="info.desc" />
			</div>
		</div>
		<hr class="line" />
		<div class="content-container">
			<div class="type-container">
				<h1>{{ $t("resumeView.skills.mySkills") }}</h1>
			</div>
			<div class="resume-progress-bar-container">
				<ProgressBar v-for="skill in processedSkills" :key="skill.type" :type="skill.type" :percentage="skill.percentage" :skills="skill.skills" />
			</div>
		</div>
	</div>
</template>

<script>
import { useRoute } from "vue-router";

import ResumeInfo from "../components/ResumeInfo.vue";
import ProgressBar from "../components/ProgressBar.vue";

import EducationIcon from "../components/svgs/EducationIcon.vue";
import WorkIcon from "../components/svgs/WorkIcon.vue";

export default {
	name: "Resume",
	components: { ResumeInfo, ProgressBar, EducationIcon, WorkIcon },
	computed: {
		route: () => useRoute(),
		processedEduInfo() {
			const eduInfo = [
				{ title: this.$i18n.t("resumeView.eduInfo.info1.title"), time: this.$i18n.t("resumeView.eduInfo.info1.time"), desc: this.$i18n.t("resumeView.eduInfo.info1.desc") },
				{ title: this.$i18n.t("resumeView.eduInfo.info2.title"), time: this.$i18n.t("resumeView.eduInfo.info2.time"), desc: this.$i18n.t("resumeView.eduInfo.info2.desc") },
				{ title: this.$i18n.t("resumeView.eduInfo.info3.title"), time: this.$i18n.t("resumeView.eduInfo.info3.time"), desc: this.$i18n.t("resumeView.eduInfo.info3.desc") },
			];

			return eduInfo;
		},
		processedWorkInfo() {
			const workInfo = [{ title: this.$i18n.t("resumeView.workInfo.info1.title"), time: this.$i18n.t("resumeView.workInfo.info1.time"), desc: this.$i18n.t("resumeView.workInfo.info1.desc") }];

			return workInfo;
		},
		processedSkills() {
			const skills = [
				{ type: this.$i18n.t("resumeView.skills.type.webDev"), percentage: "90", skills: ["HTML", "CSS", "Javascript", "VueJs", "NestJs", "PHP"] },
				{ type: this.$i18n.t("resumeView.skills.type.webDesign"), percentage: "80", skills: ["Adobe Illustrator", "Figma", "WebFlow"] },
				{ type: this.$i18n.t("resumeView.skills.type.design3D"), percentage: "80", skills: ["Blender", "Autodesk Maya", "Adobe Substance Painter"] },
				{ type: this.$i18n.t("resumeView.skills.type.graphicDesign"), percentage: "70", skills: ["Adobe Photoshop", "Adobe Illustrator"] },
				{ type: this.$i18n.t("resumeView.skills.type.photo"), percentage: "60", skills: ["Adobe Lightroom", "Adobe Photoshop"] },
			];

			return skills;
		},
	},
};
</script>
