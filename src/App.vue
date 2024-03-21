<template>
	<div class="grid-container">
		<div class="grid-left-side">
			<Profile />
		</div>
		<div class="grid-right-side">
			<Nav />
			<router-view />
		</div>
	</div>
</template>

<script>
import Profile from "./components/Profile.vue";
import Nav from "./components/Nav.vue";

export default {
	name: "App",
	components: { Nav, Profile },
};
</script>
