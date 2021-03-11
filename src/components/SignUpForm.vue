<template>
	<form>
		<label>Email:</label>
		<input type="email" required v-model="email" />
		<label>Password:</label>
		<input type="password" required v-model="password" />
		<label>Role:</label>
		<select v-model="role">
			<option value="developer">Web Developer</option>
			<option value="designer">Web Designer</option>
		</select>

		<div class="terms">
			<label>Accept Terms & Conditions</label>
			<input type="checkbox" v-model="terms" required />
		</div>
		<!-- OPTIONS ARRAY -->
		<label>Options:</label>
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
	</form>
	<h2>Demonstrating Two-way Data Binding:</h2>
	<p>Email:</p>
	<span id="special">{{ email }}</span>
	<p>Password:</p>
	<span id="special">{{ password }}</span>
	<p>Role:</p>
	<span id="special">{{ role }}</span>
	<p>Terms Accepted:</p>
	<span id="special">{{ terms }}</span>
	<p>Options Selected:</p>
	<span id="special">{{ options }}</span>
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
		};
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
</style>
