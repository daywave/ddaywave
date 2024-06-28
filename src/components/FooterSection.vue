<template>
  <div class="footer-section">
    <div class="content">
      <div class="contact-info">
        <h3>Contact Info</h3>
        <p><i class="fas fa-map-marker-alt"></i> Aguascalientes, Aguascalientes, México.</p>
        <p><i class="fas fa-envelope"></i> djjceja@gmail.com</p>
        <p><i class="fas fa-globe"></i> ddaywave.com</p>
        <h3>Follow Me</h3>
        <div class="social-links">
          <a href="https://github.com/daywave" target="_blank"><i class="fab fa-github"></i></a>
          <a href="https://linkedin.com/in/donovan-jerez-ceja" target="_blank"><i class="fab fa-linkedin"></i></a>
        </div>
      </div>
      <div class="contact-form">
        <h3>Contact Form</h3>
        <form @submit.prevent="sendEmail" id="form">
          <div class="form-group">
            <label for="from_name">Name: </label>
            <input type="text" v-model="form.from_name" name="from_name" id="from_name" required>
          </div>
          <div class="form-group">
            <label for="email">Email</label>
            <input type="email" v-model="form.email_id" name="email" id="email" required>
          </div>
          <div class="form-group">
            <label for="message">Message</label>
            <textarea v-model="form.message" name="message" id="message" required></textarea>
          </div>
          <input type="submit" id="button" :value="buttonText" class="send-button">
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import emailjs from 'emailjs-com';

export default {
  data() {
    return {
      form: {
        from_name: '',
        message: '',
        email: ''
      },
      buttonText: 'Send Email'
    };
  },
  methods: {
    sendEmail() {
      this.buttonText = 'Sending...';

      const serviceID = 'personal_web';
      const templateID = 'template_mc8stsx';
      const userID = 'mispQotRPnEwtX_mJ';

      emailjs.sendForm(serviceID, templateID, '#form', userID)
        .then(() => {
          this.buttonText = 'Send Email';
          alert('Sent!');
          this.resetForm();
        }, (err) => {
          this.buttonText = 'Send Email';
          alert(JSON.stringify(err));
        });
    },
    resetForm() {
      this.form.from_name = '';
      this.form.email = '';
      this.form.message = '';
    }
  }
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;700&display=swap');

.footer-section {
  background-color: #000000;
  color: #c5c8c6;
  padding: 4rem 2rem;
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: 'Fira Code', monospace;
}

.content {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  max-width: 1200px;
  width: 100%;
}

.contact-info, .contact-form {
  flex: 1;
  margin: 0 1rem;
  min-width: 280px;
}

.contact-info h3, .contact-form h3 {
  margin-bottom: 1rem;
  color: #6DA5C0;
  position: relative;
}

.contact-info h3::after, .contact-form h3::after {
  content: '';
  width: 50px;
  height: 4px;
  background-color: #6DA5C0;
  position: absolute;
  bottom: -10px;
  left: 0;
  box-shadow: 0 0 5px #6DA5C0, 0 0 10px #6DA5C0, 0 0 20px #6DA5C0, 0 0 40px #6DA5C0, 0 0 80px #6DA5C0;
}

.contact-info p {
  margin: 0.5rem 0;
}

.contact-info i {
  margin-right: 0.5rem;
  color: #6DA5C0;
}

.social-links a {
  color: #6DA5C0;
  margin-right: 1rem;
  text-decoration: none;
  transition: color 0.3s ease;
}

.social-links a:hover {
  color: #0C7075;
}

.contact-form form {
  display: flex;
  flex-direction: column;
}

.contact-form .form-group {
  margin-bottom: 1rem;
}

.contact-form label {
  display: block;
  margin-bottom: 0.5rem;
}

.contact-form input, .contact-form textarea {
  width: 100%;
  padding: 0.75rem;
  border: none;
  border-radius: 4px;
  background-color: #1b1e34;
  color: #c5c8c6;
  margin-bottom: 0.5rem;
  transition: background-color 0.3s ease, color 0.3s ease;
}

.contact-form input:focus, .contact-form textarea:focus {
  background-color: #101223;
  color: #ffffff;
}

.contact-form .send-button {
  padding: 0.75rem 1.5rem;
  background-color: #1b1e34;
  border: none;
  border-radius: 4px;
  color: white;
  cursor: pointer;
  align-self: flex-start;
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.contact-form .send-button:hover {
  background-color: #0C7075;
  transform: translateY(-3px);
}
</style>
