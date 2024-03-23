<template>
	<NavBar />
	<div class="grid-container">
		<div class="grid-left-side">
			<Profile />
		</div>
		<div class="grid-right-side">
			<router-view />
		</div>
	</div>
</template>

<script>
import Profile from "./components/Profile.vue";
import NavBar from "./components/NavBar.vue";

export default {
	name: "App",
	components: { NavBar, Profile },
};
</script>
