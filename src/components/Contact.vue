<template>
  <section class="form-container fadeIn" ref="contactSection">
    <div class="section-header">
        <div class="section-header-small">
          <h5>Contact</h5>
          <div class="header-line"></div>
        </div>
        <h2>Contact <span class="highlight">Us</span></h2>
    </div>
    <form class="contact-form">
      <div class="contact-words">
      <div class="contact-info">
        <img src="../assets/icons/location.svg" alt="Location"/>
        <div>
          <h4>Location</h4>
          <p>City, state</p>
        </div>
      </div>
      <div class="contact-info">
        <img src="../assets/icons/phone.svg" alt="Phone"/>
        <div>
          <h4>Phone</h4>
          <p>(123) 345-5678</p>
        </div>
      </div>
      <div class="contact-info">
        <img src="../assets/icons/email.svg" alt="Email"/>
        <div>
          <h4>Email</h4>
          <p>Email@email.com</p>
        </div>
      </div>
      </div>
      <div class="form-content">
      <div class="half-width">
        <input
          type="text"
          id="nameInput"
          class="input"
          placeholder="Name..."
          aria-label="Name..."
          required
        />
        <input
          type="email"
          id="emailInput"
          class="input"
          placeholder="Email..."
          aria-label="Email..."
          required
        />
      </div>
      <input
        type="text"
        id="budgetInput"
        class="input"
        placeholder="What is your Budget for this project?"
        aria-label="What is your Budget for this project?"
        required
      />
      <input
        type="text"
        id="helpInput"
        class="input"
        placeholder="How can we help?"
        aria-label="How can we help?"
        required
      />
      <button type="submit" class="btn-primary full-width">Submit</button>
      </div>
    </form>
  </section>
</template>

<script>
export default {
  name: "ContactComponent",
  mounted() {
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          this.$refs.contactSection.classList.add('fadeIn-visible');
          observer.unobserve(this.$refs.contactSection); // Stop observing once it's visible
        }
      });
    }, {
      threshold: 0.1 // Adjust as needed
    });

    observer.observe(this.$refs.contactSection);
  }
};
</script>

<style scoped>

@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

.fadeIn {
  opacity: 0; /* Initial hidden state */
  transition: opacity 1s ease-in-out;
}

.fadeIn.fadeIn-visible {
  opacity: 1; /* Visible state */
}

.form-container {
  background-color: #f5f9ff;
  width: 100%;
  padding: 120px 64px;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  position: relative;
  gap: 40px;
  box-sizing: border-box;
}

.contact-words{
  display: flex;
  flex-direction: column;
  width: 30%;
  flex: 1;
  justify-content: space-between;
}

.contact-info p {
  font-size: 16px;
}

.contact-info div {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.contact-info {
  display: flex;
  gap: 16px;
  align-items: center;
  width: 100%;
}

.form-content {
  display: flex;
  flex-direction: column;
  gap: 32px;
  width: 60%;
}

.half-width {
  display: flex;
  justify-content: space-between;
  width: 100%;
  flex-direction: row;
  gap: 0px;
}

.half-width input {
  width: 45%;
}

.contact-form {
  display: flex;
  flex-wrap: wrap;
  gap: 32px;
  width: 100%;
  background-color: white;
  padding: 32px;
  border-radius: 32px;
  box-sizing: border-box;
  z-index: 2;
}

.input {
  padding: 12px 0;
  border: none;
  border-bottom: 2px solid rgba(136, 136, 136, 0.2);
  font: 16px Segoe UI, sans-serif;
  box-sizing: border-box;
}

.input:focus {
  outline: none;
  border-bottom-color: #4173F3;
}

.btn-primary {
  background-color: #4173F3;
  color: #fff;
  border-radius: 8px;
  padding: 12px 32px;
  border: none;
  z-index: 2;
  cursor: pointer;
  width: 100%;
}

.btn-primary:hover {
  background-color: #003B80;
}

.top-right-corner-image {
  position: absolute;
  top: 0;
  right: 0;
  width: 30%;
}

.bottom-left-corner-image {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 30%;
}

.full-width {
  width: 100%;
}

@media (max-width: 800px) {

  .half-width {
    flex-direction: column;
    gap: 32px;
  }

  .half-width input {
    width: 100%;
  }

  .form-container {
    padding: 20px;
  }
  .contact-words{
    width: 100%;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    gap: 16px;
  }
  .contact-info {
    width: 30%;
  }

  .form-content {
    width: 100%;
  }
}

@media (max-width: 600px) {

  .contact-words{
    justify-content: flex-start;
  }

  .contact-info img {
    width: 24px;
  }

  .contact-info {
    width: 47%;
  }
}

</style>
