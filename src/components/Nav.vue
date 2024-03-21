<template>
	<div class="nav-grid-container">
		<div class="nav-grid-left-side">
			<router-link :to="{ name: 'about' }">{{ $t("nav.about") }}</router-link>
			<router-link :to="{ name: 'resume' }">{{ $t("nav.resume") }}</router-link>
			<router-link :to="{ name: 'portfolio' }">{{ $t("nav.portfolio") }}</router-link>
		</div>
		<div class="nav-grid-right-side">
			<div class="locale-changer">
				<select v-model="$i18n.locale">
					<option selected value="hr">Hrvatski</option>
					<option value="en">English</option>
				</select>
			</div>
			<!-- <div class="theme-switch-wrapper">
				<label class="theme-switch" for="checkbox">
					<input type="checkbox" id="checkbox" @change="switchTheme()" />
					<div class="slider round"></div>
				</label>
			</div> -->
			<div class="theme-switch-container">
				<img :src="require('../assets/' + this.themeIcon + '-icon.svg')" @click="switchTheme" />
				<!-- <img v-if="!this.switchedTheme" src="../assets/moon-icon.svg" @click="switchTheme" />
				<img v-if="this.switchedTheme" src="../assets/sun-icon.svg" @click="switchTheme" /> -->
			</div>
		</div>
	</div>
</template>

<script>
document.documentElement.setAttribute("data-theme", "dark");

export default {
	name: "App",
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
