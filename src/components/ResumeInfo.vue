<template>
	<div class="resume-info-container">
		<div class="resume-info-title">{{ title }}</div>
		<div class="resume-info-time">{{ time }}</div>
		<div class="resume-info-desc">{{ desc }}</div>
	</div>
</template>

<script>
export default {
	props: ["title", "time", "desc"],
};
</script>
