<template>
  <div>
    
  </div>
</template>
<script>
import axios from 'axios'
export default {
  components : { },
  data () {
    return {
      // api_key: "key=lAYuyhutioeCVRvHVSZgBC8wf8CPcO0E",
      api_key: "key=OwsqVQlIWGAZAkomcYI0rDYG2tDpmRPE",
      baseUrl: "https://api.tomtom.com/search/2/structuredGeocode.json?",

      queryParams : {
        countryCode: "IT",
        limit: 1, //default,
        streetNumber: "4/43",
        streetName: "via michelangelo",
        municipality: "caltanissetta",
        municipalitySubdivision: "",
        countryTertiarySubdivision: "",
        countrySecondarySubdivision: "",
        countrySubdivision: "",
        postalCode: "93100",
        entityTypeSet: "",


        

      }

    }
  },
  methods: {
    fecthTomTom() {

      // axios.get("https://api.tomtom.com/search/2/geocode/De%20Ruijterkade%20154,%201011%20AC,%20Amsterdam.json?key=lAYuyhutioeCVRvHVSZgBC8wf8CPcO0E").then((resp) => {
      axios.get(this.baseUrl + this.api_key , {
        params : this.queryParams
      })
      .then((resp) =>  {
        console.log(resp);
        console.log(resp.data.results[0].address.freeformAddress);
        console.log(resp.data.results[0].position.lat);
        console.log(resp.data.results[0].position.lon);
      })
       
    
    },
  },
  mounted() {
    this.fecthTomTom()
  },
  
}
</script>
<style lang="">
  
</style>