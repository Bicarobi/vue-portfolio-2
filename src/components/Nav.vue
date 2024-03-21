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
			<div class="theme-switch-wrapper">
				<label class="theme-switch" for="checkbox">
					<input type="checkbox" id="checkbox" @change="switchTheme()" />
					<div class="slider round"></div>
				</label>
			</div>
		</div>
	</div>
</template>

<script>
var switchTheme = false;
document.documentElement.setAttribute("data-theme", "dark");

export default {
	name: "App",
	methods: {
		switchTheme() {
			if (switchTheme) {
				document.documentElement.setAttribute("data-theme", "dark");
			} else {
				document.documentElement.setAttribute("data-theme", "light");
			}
			switchTheme = !switchTheme;
		},
	},
};
</script>
