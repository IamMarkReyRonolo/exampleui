<template>
	<div class="signUpPage">
		<v-row align="center" justify="center">
			<v-col lg="10" sm="11" cols="11">
				<div class="imgCon">
					<img src="../assets/logo.png" alt="" class="logo" />
				</div>

				<v-card class="signUp" min-height="600px">
					<div class="con">
						<h1>Register</h1>
						<br />
						<br />
						<v-form v-model="valid" ref="form" lazy-validation>
							<v-row justify="center">
								<v-col lg="5" cols="11" sm="6"
									><v-text-field
										filled
										placeholder="First Name"
										prepend-inner-icon="mdi-contacts"
										v-model="fname"
										:rules="fnameRules"
									></v-text-field>
									<v-text-field
										filled
										placeholder="Middle Name"
										prepend-inner-icon="mdi-contacts"
										v-model="mname"
									></v-text-field>
									<v-text-field
										filled
										placeholder="Last Name"
										prepend-inner-icon="mdi-contacts"
										v-model="lname"
										:rules="lnameRules"
									></v-text-field>
									<v-text-field
										filled
										placeholder="Phone Number"
										prepend-inner-icon="mdi-card-account-phone-outline"
										v-model="phone"
										:rules="phoneRules"
									></v-text-field>
								</v-col>
								<v-col lg="5" cols="11" sm="6"
									><v-text-field
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
									<v-text-field
										filled
										placeholder="Repeat Password"
										prepend-inner-icon="mdi-shield-lock"
										:type="show2 ? 'text' : 'password'"
										:append-icon="show2 ? 'mdi-eye' : 'mdi-eye-off'"
										@click:append="show2 = !show2"
										v-model="rpassword"
										:rules="
											this.rpassword != this.password
												? passMatch
												: passwordRules
										"
									></v-text-field>

									<v-textarea
										solo
										name="input-7-4"
										label="Message Box"
									></v-textarea>
								</v-col>
							</v-row>
						</v-form>

						<v-btn xl @click="signUp">Create My Account</v-btn>
						<v-row justify="center">
							<v-col lg="8" sm="10" cols="12">
								<div class="terms">
									<p>
										By clicking "Create My Account" you agree to our terms and
										conditions.
									</p>
									<p>
										Lorem ipsum dolor sit amet consectetur, adipisicing elit.
										Modi quae, in impedit similique atque itaque excepturi sed
										et ducimus nobis? Lorem ipsum, dolor sit amet consectetur
										adipisicing elit. Corporis similique, sunt totam fugit quis
										cum ex illo incidunt quibusdam neque.
									</p>
								</div>
							</v-col>
						</v-row>

						<br />
						<p>Already have an account?</p>

						<v-btn xl to="/signin">Sign In Instead</v-btn>
					</div>
				</v-card>
				<br />
				<br
			/></v-col>
		</v-row>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				valid: true,
				show1: false,
				fname: "",
				mname: "",
				lname: "",
				phone: "",
				email: "",
				password: "",
				rpassword: "",
				show1: false,
				show2: false,
				fnameRules: [(v) => !!v || "First name is required"],
				lnameRules: [(v) => !!v || "Last name is required"],
				phoneRules: [
					(v) => !!v || "Phone is required",
					(v) =>
						/^\(?([0-9]{3})\)?[-. ]?([0-9]{3})[-. ]?([0-9]{4})$/.test(v) ||
						"Phone must be valid (XXX-XXX-XXXX)",
				],
				emailRules: [
					(v) => !!v || "E-mail is required",
					(v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
				],
				passwordRules: [
					(v) => !!v || "Password is required",
					(v) =>
						/^(?=.*?[A-Z])/.test(v) ||
						"Password must have atleast one uppercase letter",
					(v) =>
						/^(?=.*?[a-z])/.test(v) ||
						"Password must have atleast one lowercase letter",
					(v) =>
						/^(?=.*?[0-9])/.test(v) || "Password must have atleast one number",
					(v) =>
						/^(?=.*?[#?!@$%^&*-])/.test(v) ||
						"Password must have atleast one character",

					(v) => v.length > 10 || "Min 11 characters",
				],
				passMatch: [() => `The password you entered don't match`],
			};
		},
		methods: {
			signUp() {
				if (this.$refs.form.validate()) {
					console.log(this.email);
					console.log(this.password);
				}
			},
		},
	};
</script>

<style scoped>
	.signUp {
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

	.terms {
		text-align: justify;
		padding: 10px;
		margin: 20px;
		border-radius: 5px;
		background-color: rgb(255, 255, 255);
		box-shadow: 0px 3px 1px -2px rgba(0, 0, 0, 0.2),
			0px 2px 2px 0px rgba(0, 0, 0, 0.14), 0px 1px 5px 0px rgba(0, 0, 0, 0.12);
	}

	.terms p {
		font-size: 12px;
		padding: 5px;
		margin: 0px;
	}
</style>
