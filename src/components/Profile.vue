<template>
	<div class="profile-container">
		<div class="grid-container">
			<div class="grid-left-side">
				<div class="grid-container">
					<div class="grid-left-side">
						<router-link :to="{ name: 'about' }"><img src="../assets/profile-image-2.jpg" /></router-link>
					</div>
					<div class="grid-right-side">
						<div class="name">Robert Cmrečki</div>

						<div class="tag-container">
							<router-link :to="{ name: 'portfolio', params: { filter: 'web-dev' } }"
								><div class="tag">{{ $t("profile.skills.webDev") }}</div></router-link
							>
							<router-link :to="{ name: 'portfolio', params: { filter: 'web-design' } }"
								><div class="tag">{{ $t("profile.skills.webDesign") }}</div></router-link
							>
							<router-link :to="{ name: 'portfolio', params: { filter: '3d-design' } }"
								><div class="tag">{{ $t("profile.skills.design3D") }}</div></router-link
							>
							<router-link :to="{ name: 'portfolio', params: { filter: 'graphic-design' } }"
								><div class="tag">{{ $t("profile.skills.graphicDesign") }}</div></router-link
							>
							<!-- <router-link :to="{ name: 'portfolio', params: { filter: 'photography' } }"><div class="tag">Photographer</div></router-link> -->
						</div>
					</div>
				</div>

				<!-- <a class="title" href="https://urn.nsk.hr/urn:nbn:hr:122:388921"><h3>bacc. ing. techn. graph.</h3></a> -->
				<div class="profile-info-container" :style="{ display: openedProfile || this.$myGlobalVariable.windowWidth > this.$myGlobalVariable.mobileWindowWidth ? 'flex' : 'none' }">
					<hr class="line" />

					<div class="info-container">
						<ProfileInfoTag v-for="tag in processedTags" :key="tag.type" :type="tag.type" :description="tag.description" :link="tag.link">
							<component :is="tag.image" />
						</ProfileInfoTag>
					</div>
					<hr class="line" />
					<div class="social-container">
						<a href="https://www.linkedin.com/in/robert-cmrecki/" target="_blank"> <LinkedInIcon /></a>
						<a href="https://github.com/Bicarobi/" target="_blank"> <GitHubIcon /></a>
						<a href="https://www.instagram.com/ro2tsa/" target="_blank"><InstagramIcon /></a>
					</div>
				</div>
				<div class="profile-button-container" :style="{ display: this.$myGlobalVariable.windowWidth <= this.$myGlobalVariable.mobileWindowWidth ? 'block' : 'none' }">
					<ProfileButtonIcon @click="this.openProfile" :openedProfile="this.openedProfile" />
				</div>
			</div>
			<div class="grid-right-side">
				<hr class="line" />
			</div>
		</div>
	</div>
</template>

<script>
import ProfileInfoTag from "../components/ProfileInfoTag.vue";
import EmailIcon from "./svgs/EmailIcon.vue";
import PhoneIcon from "./svgs/PhoneIcon.vue";
import LocationIcon from "./svgs/LocationIcon.vue";
import LinkedInIcon from "./svgs/LinkedInIcon.vue";
import GitHubIcon from "./svgs/GitHubIcon.vue";
import InstagramIcon from "./svgs/InstagramIcon.vue";
import ProfileButtonIcon from "./svgs/ProfileButtonIcon.vue";

export default {
	name: "Profile",
	components: { ProfileInfoTag, EmailIcon, PhoneIcon, LocationIcon, LinkedInIcon, GitHubIcon, InstagramIcon, ProfileButtonIcon },
	data() {
		return {
			openedProfile: true,
		};
	},
	computed: {
		processedTags() {
			const tags = [
				{ type: "email", description: "cmrecki.robert@&#8203;gmail.com", image: "EmailIcon", link: "mailto:cmrecki.robert@gmail.com" },
				{ type: "phone", description: "+385 91 211 1165", image: "PhoneIcon", link: "tel:0912111165" },
				{ type: "location", description: " / Varaždin", image: "LocationIcon", link: "https://maps.app.goo.gl/3qw2hEo96L59ebqo9" },
			];

			return tags.map((tag) => {
				if (tag.type == "email") {
					const parsed = new DOMParser().parseFromString(tag.description, "text/html").body.textContent;
					tag.description = parsed;
				}

				if (tag.type == "phone") {
					tag.type = this.$i18n.t("profile.phone");
				}

				if (tag.type == "location") {
					tag.type = this.$i18n.t("profile.location");

					tag.description = this.$i18n.t("profile.location2") + " / Varaždin";
				}
				return {
					type: tag.type,
					description: tag.description,
					image: tag.image,
					link: tag.link,
				};
			});
		},
	},
	beforeMount() {
		if (localStorage.openedProfile == "enabled") {
			this.openedProfile = true;
		} else {
			this.openedProfile = false;
		}
		this.openProfile();
	},
	methods: {
		openProfile() {
			if (this.openedProfile) {
				localStorage.openedProfile = "enabled";
			} else {
				localStorage.openedProfile = "disabled";
			}
			this.openedProfile = !this.openedProfile;
		},
	},
};
</script>
