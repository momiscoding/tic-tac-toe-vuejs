<template>
  <footer class="footer mt-auto bg-light">
    <div class="row">
      <div class="col-lg-4 col-md-6 mb-4 mb-md-0">
        <h6>About page</h6>
        <ul class="nav flex-column">
          <li class="nav-item mb-2">
            Play tic tac toe or 4-in-a-row anytime!
          </li>
          <li class="nav-item mb-2">
            Created by Ana Russo
          </li>
        </ul>
      </div>

      <div class="col-lg-4 col-md-6 mb-4 mb-md-0">
        <h6>Contacts</h6>
        <ul class="nav flex-column">
          <li class="nav-item mb-2">
            (+351) 123 456 789
          </li>
          <li class="nav-item mb-2">
            Rua Sá da Bandeira, 111, Porto
          </li>
        </ul>
      </div>

      <div class="col-lg-4 col-md-6 mb-4 mb-md-0">
        <h6>Stay in touch</h6>
        <ul class="nav list-unstyled">
          <li>
            <a class="text-muted" href="#"
              ><img
                src="/public/assets/img/facebook.svg"
                alt="Facebook Logo"
                class="facebook-icon"
            /></a>
          </li>
          <li>
            <a class="text-muted" href="#"
              ><img
                src="/public/assets/img/twitter.svg"
                alt="Twitter Logo"
                class="twitter-icon"
            /></a>
          </li>
          <li>
            <a class="text-muted" href="#"
              ><img
                src="/public/assets/img/instagram.svg"
                alt="Instagram Logo"
                class="instagram-icon"
            /></a>
          </li>
        </ul>
        <form
          id="app"
          @submit="checkForm()"
          action="https://google.com/"
          method="post"
        >
          <div class="input-group mb-3">
            <input
              type="email"
              v-model="email"
              class="form-control"
              placeholder="Subscribe our games"
              aria-label="Subscribe our games"
              aria-describedby="button-addon"
            />
            <button
              class="btn btn-outline-secondary"
              id="button-addon"
              type="submit"
              value="Submit"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="16"
                height="16"
                fill="currentColor"
                class="bi bi-send"
                viewBox="0 0 16 16"
              >
                <path
                  fill-rule="evenodd"
                  d="M15.854.146a.5.5 0 0 1 .11.54l-5.819 14.547a.75.75 0 0 1-1.329.124l-3.178-4.995L.643 7.184a.75.75 0 0 1 .124-1.33L15.314.037a.5.5 0 0 1 .54.11ZM6.636 10.07l2.761 4.338L14.13 2.576 6.636 10.07Zm6.787-8.201L1.591 6.602l4.339 2.76 7.494-7.493Z"
                ></path>
              </svg>
            </button>
          </div>
        </form>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  data() {
    return {
      email: ""
    };
  },

  checkForm: function(e) {
    this.errors = [];

    if (!this.email) {
      this.errors.push("Email required.");
    } else if (!this.validEmail(this.email)) {
      this.errors.push("Valid email required.");
    }

    if (!this.errors.length) {
      return true;
    }

    e.preventDefault();
  },
  validEmail: function(email) {
    var re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
    return re.test(email);
  }
};
</script>

<style>
.footer {
  padding: 60px 150px;

  
}

.footer ul {
  justify-content: center;
  font-size: 14px;
  margin-bottom: 15px;
}

.footer ul > li {
  margin-left: 0;
}

.footer li.nav-item {
  margin: 0;
}

.footer img {
  width: 24px;
  opacity: 0.6;
  transition: 0.5s ease-in-out;
}

.footer img:hover {
  width: 24px;
  opacity: 1;
}

@media only screen and (min-width: 768px) {
  .footer {
    text-align: left;
  }
  .footer ul {
    justify-content: left;
  }
}
</style>
