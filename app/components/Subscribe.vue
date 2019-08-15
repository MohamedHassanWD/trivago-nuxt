<template>
  <div class="row">
    <div class="columns">
      <div class="column" id="text">
        <h2>You Love Travel, huh?</h2>
        <p>Subscribe now to get all the new posts, offers and destinations to your passion.</p>
      </div>
      <div class="column" id="form">
        <b-field :type="{'is-danger': errors.has('email')}" :message="errors.first('email')">
          <b-input
            type="email"
            name="email"
            v-validate="'required|email'"
            v-model="emailAddress"
            placeholder="Your Email Address"
            class="email-field"
          />
        </b-field>
        <b-button
          @click.prevent="handleSubscribe"
          :loading="buttonClicked"
          class="button is-primary"
          style="width: 100%;"
        >Subscribe</b-button>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from "vue";
// You have to install VeeValidate to use it:
// 'npm install vee-validate'
import VeeValidate from "vee-validate";

Vue.use(VeeValidate, {
  events: ""
});
export default {
  name: "Subscribe",
  data() {
    return {
      buttonClicked: false,
      emailAddress: null
    };
  },
  methods: {
    handleSubscribe() {
      this.$validator.validateAll().then(result => {
        if (result) {
          this.$buefy.toast.open({
            message: "Subscribed Successfully!",
            type: "is-success",
            position: "is-top-right"
          });
          return;
        }
        this.$buefy.toast.open({
          message: "You didn't enter a valid email address",
          type: "is-danger",
          position: "is-top-right"
        });
      });
    }
  }
};
</script>

<style scoped>
.row {
  margin: 30px 0;
  padding: 100px 20px;
  background: #96c3ea;
  background-image: url("../assets/cut-surfer.png");
  background-repeat: no-repeat;
  background-size: 400px;
  background-position-y: bottom;
}
#text {
  text-align: center;
  font-weight: bold;
  color: #fff;
  text-shadow: 3px 3px 0 rgba(173, 173, 173, 0.2), 3px 3px 3px #000000; /* FF3.5+, Opera 9+, Saf1+, Chrome, IE10 */
}
#form {
  margin: 0 auto;
  display: block;
  padding: 20px;
}
.email-field .input {
  display: block;
  width: 100%;
  font-size: 1.5rem;
  outline: none;
  padding: 20px;
  border: 1px solid #ccc;
}
.email-field .input:focus {
  border: 1px solid #330;
}
.button {
  margin: 20px 0;
  text-transform: uppercase;
}
</style>
