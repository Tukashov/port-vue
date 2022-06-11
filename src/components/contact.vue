<template>
  <div class="home">
   <!-- Contact -->
		<section class="container contact" id="contact">
			<div class="row">
				<div class="col-md-12">
					<h3 class="text-center"><span>04. What's Next ?</span></h3>
					<h3 class="text-center get">Get In Touch</h3>
				</div>
				<div class="col-md-8 offset-md-2">
					<p class="text-center">I'm currently looking for job opporunities. Kindly reach out to me if there are any. And if it is just to say hi, my inbox is always open. I will reply as soon as possible.</p>
				</div>
				<div class="col-md-8 offset-md-2">
					<form method="POST" @submit.prevent="submit">
						<div class="mb-3">
								<p for="fullName" class="form-label">Full Name</p>
								<input required v-model="fullName" type="name" class="form-control" id="fullName" aria-describedby="name" placeholder="Your Name">
							</div>
							<div class="mb-3">
								<p for="exampleInputEmail1" class="form-label">Email</p>
								<input required v-model="email" type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Your Email">
							</div>
							<div class="mb-3">
								<p for="subject" class="form-label">Subject</p>
								<input required v-model="subject" type="subject" class="form-control" id="subject" placeholder="Subject">
							</div>
							<div class="mb-3">
								<p for="message" class="form-label">Message</p>
								<textarea required v-model="message" class="form-control" id="message" rows="3"></textarea>
							</div>
							<button type="submit" class="btn btn-primary">Send Message</button>
					</form>
				</div>
			</div>
		</section>
  </div>
</template>

<script>
export default {
	data() {
		return {
			fullName: '',
			email: '',
			subject: '',
			message: '',
			
			token: '5346590183:AAFjOFPcbLyDKTVmvbUMBadvNXsjqI_WJYs',
			chatId: 652693109,
		}
	},

	methods: {
		submit() {
			const fullMassage = `Name: ${this.fullName}\nEmail: ${this.email}\nSubject: ${this.subject}\nMessage: ${this.message}`;
			this.$http.post(`https://api.telegram.org/bot${this.token}/sendMessage?chat_id=${this.chatId}&text=${fullMassage}`)
			.then (response => {
				alert("Submitted!🎉", response);
			}, error => {
				console.log(error);
			});
		}
	}
}
</script>

<style scoped>
.btn {
	background: #64ffda;
	color: #000;
	border: 0;
}

.btn:hover {
	background: #64ffdbe7;
	color: #000;
}
</style>