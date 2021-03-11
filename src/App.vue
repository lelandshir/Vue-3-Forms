<template>
	<h1>Vue Project 1.3: Forms</h1>
	<SignUpForm />
</template>

<script>
import SignUpForm from "./components/SignUpForm.vue";

export default {
	name: "App",
	components: { SignUpForm },
};
</script>

<style lang="sass">
@import "./styles/global.sass"
</style>
