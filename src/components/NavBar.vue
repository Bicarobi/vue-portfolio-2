<template>
	<div class="nav-grid-container">
		<div class="nav-grid-left-side">
			<router-link :to="{ name: 'about' }">{{ $t("navBar.about") }}</router-link>
			<router-link :to="{ name: 'resume' }">{{ $t("navBar.resume") }}</router-link>
			<router-link :to="{ name: 'portfolio' }">{{ $t("navBar.portfolio") }}</router-link>
		</div>
		<div class="nav-grid-right-side">
			<div class="locale-changer">
				<select v-model="$i18n.locale">
					<option selected value="hr">Hrvatski</option>
					<option value="en">English</option>
				</select>
			</div>
			<div class="theme-switch-container">
				<ThemeIcon :switchedTheme="this.switchedTheme" @click="switchTheme" />
			</div>
		</div>
	</div>
</template>

<script>
import ThemeIcon from "../components/svgs/ThemeIcon.vue";

document.documentElement.setAttribute("data-theme", "dark");

export default {
	name: "NavBar",
	components: { ThemeIcon },
	data() {
		return {
			switchedTheme: false,
			themeIcon: "moon",
		};
	},
	methods: {
		switchTheme() {
			if (this.switchedTheme) {
				document.documentElement.setAttribute("data-theme", "dark");
				this.themeIcon = "moon";
			} else {
				document.documentElement.setAttribute("data-theme", "light");
				this.themeIcon = "sun";
			}
			this.switchedTheme = !this.switchedTheme;
		},
	},
};
</script>
