<template>
	<!-- FORM -->
	<form @submit.prevent="handleSubmit">
		<b>User Credentials:</b>
		<br />
		<label>Email:</label>
		<input type="email" required v-model="email" />
		<label>Password:</label>
		<input type="password" required v-model="password" />
		<div v-if="passwordError" id="error">{{ passwordError }}</div>
		<label>Role:</label>
		<select v-model="role">
			<option value="developer">Web Developer</option>
			<option value="designer">Web Designer</option>
		</select>
		<!-- SKILLS -->
		<label>Skills</label>
		<input type="text" v-model="tempSkill" @keyup="addSkill" />
		<div v-for="skill in skills" :key="skill" class="pill">
			<!-- using v-for, we have access to the skill / pass into method attd to @click -->
			<span @click="deleteSkill(skill)">{{ skill }}</span>
		</div>

		<div class="terms">
			<label>Accept Terms & Conditions</label>
			<input type="checkbox" v-model="terms" required />
		</div>
		<br />
		<!-- OPTIONS ARRAY -->
		<b>User Options:</b>
		<div>
			<label>Zendesk Training Module</label>
			<input type="checkbox" value="ZTM" v-model="options" />
		</div>

		<div>
			<label>Slack Workspace</label>
			<input type="checkbox" value="Slack" v-model="options" />
		</div>

		<div>
			<label>Envoy Calendar</label>
			<input type="checkbox" value="Calendar" v-model="options" />
		</div>
		<div class="submit"><button>Create Account</button></div>
	</form>
	<!-- FORM ENDS -->
	<!-- Demonstration Area -->
	<article>
		<h2>Demonstrating Two-way Data Binding:</h2>
		<b>Email:</b><br />
		<span id="special">{{ email }}</span
		><br />
		<b>Password:</b><br />
		<span id="special">{{ password }}</span
		><br />
		<b>Role:</b><br />
		<span id="special">{{ role }}</span
		><br />
		<b>Terms Accepted:</b><br />
		<span id="special">{{ terms }}</span
		><br />
		<b>Options Selected:</b><br />
		<span id="special">{{ options }}</span>
	</article>
</template>

<script>
export default {
	data() {
		return {
			// two-way data binding, what is here is in the inputs & vice-versa
			email: "yourname@goenvoy.co",
			password: "",
			role: "",
			terms: false,
			options: [],
			tempSkill: "",
			skills: [],
			passwordError: "",
		};
	},
	methods: {
		addSkill(e) {
			console.log(e);
			if (e.key === "," && this.tempSkill) {
				if (!this.skills.includes(this.tempSkill)) {
					this.skills.push(this.tempSkill.replace(",", ""));
				}
				this.tempSkill = "";
			}
		},
		deleteSkill(skill) {
			this.skills = this.skills.filter((item) => {
				return skill !== item;
			});
		},
		handleSubmit(e) {
			console.log("Form Submitted");
			//Validate Password
			this.passwordError =
				this.password.length > 5
					? ""
					: "password must be at least 6 character long";

			if (!this.passwordError) {
				const newUser = {
					email: this.email,
					password: this.password,
					role: this.role,
					skills: this.skills,
					options: this.options,
					terms_accepted: this.terms,
				};
				console.log(newUser);
			}
		},
	},
};
</script>

<style lang="sass">
@import "../styles/global.sass"
p
    font-weight: 700
    font-size: 1.2rem

#special
    color: $primary

form
    max-width: 420px
    margin: 30px auto
    background: #fff
    text-align: left
    padding: 40px
    border-radius: 10px

label
    color: $primary
    display: inline-block
    margin: 25px 0 15px
    font-size: 0.6em
    text-transform: uppercase
    letter-spacing: 1.5px
    font-weight: 500

input, select
    display: block
    padding: 10px 6px
    width: 100%
    box-sizing: border-box
    // sizing takes into consideration the padding and the border
    border: none
    border-bottom: 1px solid #ddd
    color: #555

input[type="checkbox"]
    display: inline-block
    width: 1rem
    margin: 0 10px 0 0
    position: relative
    top: 2px
    margin-left: 1rem
article b, form b
    color: $secondary

article b
    text-decoration: underline

.pill
    display: inline-block
    margin: 10px 10px 0 0
    padding: 6px 12px
    background: lightblue
    border-radius: 20px
    text-align: center
    font-size: 12px
    letter-spacing: 1px
    font-weight: 500
    color: $primary
    cursor: pointer
    &:hover
      background: $myDarkBlue
      color: #fff

button
    background: $primary
    border: 0
    border-radius: 20px
    padding: 10px 20px
    color: #fff
    &:hover
      cursor: pointer
      background: $myDarkBlue
      color: #fff

.submit
    text-align: center

#error
    color: red
    margin-top: 10px
    font-size: 12px
</style>
