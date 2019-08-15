<template>
  <footer id="footer">
    <div>
      <div class="columns">
        <div class="column">
          <h4>About Trivago</h4>
          <p style="text-align:left;">
            <img
              src="../assets/logo-full.svg"
              alt="Trivago"
              style="float: left;height: 20px;padding: 0 10px 0 0;margin: 0;"
            /> is a powerful global brand inspired by a transparent and authentic culture, which impacts the quality and efficiency of our daily execution. Our Mission is to be:
          </p>
          <p style="text-align:left;text-transform: capitalize;margin: 15px 0;">
            <em>The traveler’s first and independent source of information for finding the ideal hotel at the lowest rate</em>
          </p>
          <p>
            <a
              href="https://magazine.trivago.com/about/"
              target="_blank"
              class="button is-primary is-small"
            >Read More</a>
          </p>
        </div>
        <div class="column">
          <h4>Important Links</h4>
          <ul>
            <li>
              <a target="_blank" href="https://trivago.com/">Trivago</a>
            </li>
            <li>
              <a target="_blank" href="https://magazine.trivago.com/about/">About Us</a>
            </li>
            <li>
              <a target="_blank" href="https://magazine.trivago.com/contact/">Contact Us</a>
            </li>
            <li>
              <a
                target="_blank"
                href="https://www.trivago.com/app?cip=1110000000001"
              >Download Our Apps</a>
            </li>
            <li>
              <a
                target="_blank"
                href="https://www.trivago.com/privacy-policy?cip=1110000000001"
              >Privacy Policy</a>
            </li>
            <li>
              <a
                target="_blank"
                href="https://www.trivago.com/legal-information?cip=1110000000001"
              >Legal Information</a>
            </li>
          </ul>
        </div>
        <div class="column">
          <h4>Choose Your Country</h4>
          <b-field>
            <b-select
              placeholder="Select a Country"
              icon="earth"
              expanded
              v-model="selectedCountrySite"
              @input="redirectToSite"
            >
              <option
                data-hostname="magazine.trivago.it"
                id="it_IT"
                value="https://magazine.trivago.it"
              >Italia</option>
              <option
                data-hostname="magazine.trivago.es"
                id="es_ES"
                value="https://magazine.trivago.es"
              >España</option>
              <option
                data-hostname="magazine.trivago.de"
                id="de_DE"
                value="https://magazine.trivago.de"
              >Deutschland</option>
              <option
                data-hostname="magazine.trivago.fr"
                id="fr_FR"
                value="https://magazine.trivago.fr"
              >France</option>
              <option
                data-hostname="magazine.trivago.com"
                id="en_US"
                value="https://magazine.trivago.com"
              >USA</option>
              <option
                data-hostname="magazine.trivago.ca"
                id="en_CA"
                value="https://magazine.trivago.ca"
              >Canada</option>
              <option
                data-hostname="magazine.trivago.hk"
                id="zh_HK"
                value="https://magazine.trivago.hk"
              >香港</option>
              <option
                data-hostname="magazine.trivago.com.au"
                id="en_AU"
                value="https://magazine.trivago.com.au"
              >Australia</option>
              <option
                data-hostname="magazine.trivago.fi"
                id="fi"
                value="https://magazine.trivago.fi"
              >Suomi</option>
              <option
                data-hostname="magazine.trivago.com.tr"
                id="tr_TR"
                value="https://magazine.trivago.com.tr"
              >Türkiye</option>
              <option
                data-hostname="magazine.trivago.com.br"
                id="pt_BR"
                value="https://magazine.trivago.com.br"
              >Brasil</option>
              <option
                data-hostname="magazine.trivago.pt"
                id="pt_PT"
                value="https://magazine.trivago.pt"
              >Portugal</option>
              <option
                data-hostname="magazine.trivago.com.mx"
                id="es_MX"
                value="https://magazine.trivago.com.mx"
              >México</option>
              <option
                data-hostname="magazine.trivago.ie"
                id="en_IE"
                value="https://magazine.trivago.ie"
              >Ireland</option>
              <option
                data-hostname="magazine.trivago.co.uk"
                id="en_GB"
                value="https://magazine.trivago.co.uk"
              >United Kingdom</option>
              <option
                data-hostname="magazine.trivago.gr"
                id="el"
                value="https://magazine.trivago.gr"
              >Ελλάδα</option>
              <option
                data-hostname="magazine.trivago.dk"
                id="da_DK"
                value="https://magazine.trivago.dk"
              >Danmark</option>
              <option
                data-hostname="magazine.trivago.no"
                id="nb_NO"
                value="https://magazine.trivago.no"
              >Norge</option>
              <option
                data-hostname="magazine.trivago.se"
                id="sv_SE"
                value="https://magazine.trivago.se"
              >Sverige</option>
              <option
                data-hostname="magazine.trivago.sg"
                id="sg"
                value="https://magazine.trivago.sg"
              >Singapore</option>
              <option
                data-hostname="magazine.trivago.com.ar"
                id="es_AR"
                value="https://magazine.trivago.com.ar"
              >Argentina</option>
              <option
                data-hostname="magazine.trivago.nl"
                id="nl_NL"
                value="https://magazine.trivago.nl"
              >Nederland</option>
            </b-select>
          </b-field>
        </div>
        <div class="column">
          <h4>Follow Us</h4>
          <a target="_blank" href="https://www.facebook.com/trivagoUS/">
            <b-icon icon="facebook" size="is-medium"></b-icon>
          </a>
          <a target="_blank" href="https://twitter.com/trivago">
            <b-icon icon="twitter" size="is-medium"></b-icon>
          </a>
          <a target="_blank" href="https://www.instagram.com/trivago/">
            <b-icon icon="instagram" size="is-medium"></b-icon>
          </a>
        </div>
      </div>
      <div id="copyright" class="row">
        <img src="../assets/logo-white.svg" alt="Trivago Magzaine Logo" />
        <br />
        <p>
          All Rights Reserved | Copyright &copy; 2019
          <a href="#">Trivago</a>
        </p>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "Footer",
  data() {
    return {
      selectedCountrySite: null
    };
  },
  methods: {
    redirectToSite: function() {
      alert("You'll be redirected to: " + this.selectedCountrySite);
      window.location = this.selectedCountrySite;
    }
  }
};
</script>

<style>
#footer {
  background: #37454d;
  color: #fff;
  font-size: 0.85rem;
}
#footer .column {
  padding: 20px;
  text-align: center;
}
#footer a {
  color: #fff;
}
#footer a:hover {
  color: #fff;
  text-decoration: underline;
}
#copyright {
  background: #29343a;
  text-align: center;
  padding: 40px 20px;
  font-size: 0.85rem;
}
#copyright a {
  text-decoration: underline;
}
#copyright a:hover {
  text-decoration: none;
}
h4 {
  text-align: center;
  font-weight: bold;
  font-size: 1rem;
  margin: 0 0 20px 0;
}
ul li {
  list-style: none;
  margin: 0 0 10px 0;
}
</style>
