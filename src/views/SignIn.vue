<template>
	<div class="signInPage">
		<v-row align="center" justify="center">
			<v-col lg="4" sm="6" cols="11">
				<div class="imgCon">
					<img src="../assets/logo.png" alt="" class="logo" />
				</div>

				<v-card class="signIn" height="500px">
					<div class="con">
						<v-form v-model="valid" ref="form" lazy-validation>
							<h1>Sign In</h1>
							<br />
							<v-text-field
								filled
								placeholder="Email"
								prepend-inner-icon="mdi-email"
								v-model="email"
								:rules="emailRules"
							></v-text-field>
							<v-text-field
								filled
								placeholder="Password"
								prepend-inner-icon="mdi-shield-lock"
								:type="show1 ? 'text' : 'password'"
								:append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
								@click:append="show1 = !show1"
								v-model="password"
								:rules="passwordRules"
							></v-text-field>
							<br />
							<v-btn @click="signIn">Sign In</v-btn>
						</v-form>

						<br />
						<p>New to the app? Join us.</p>
						<v-btn to="/registration">Sign Up</v-btn>
						<br />
						<br />
					</div> </v-card
			></v-col>
		</v-row>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				valid: true,
				show1: false,
				email: "",
				password: "",
				emailRules: [
					(v) => !!v || "E-mail is required",
					(v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
				],
				passwordRules: [(v) => !!v || "Password is required"],
			};
		},

		methods: {
			signIn() {
				if (this.$refs.form.validate()) {
					console.log(this.email);
					console.log(this.password);
				}
			},
		},
	};
</script>

<style scoped>
	.signIn {
		padding: 20px;
	}

	.con {
		padding: 40px;
		text-align: center;
	}

	.imgCon {
		text-align: center;
	}

	.logo {
		width: 80px;
		margin: 40px auto;
	}
</style>
