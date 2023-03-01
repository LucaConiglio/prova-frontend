<template>
  <div class="container">
    <div>
      <h1>villa itria</h1>
      <div class="row gap-3">
        <div class="col-2" v-for="immagine in imgs" >
          <img  class="img-fluid mb-3" v-for="img in immagine" :src="img" alt="">
        </div>
       
        
      </div>
    </div>
    
    
  </div>
</template>
<script>
import immagini from './immagini.json'
import axios from 'axios';


export default {
  components : {},
  data () {
    return {
      imgs : immagini,
      
      
      //immagini : imgs.homes.home.url_1,
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

    // fetchsatel() {
    //   axios.post("https://hotels4.p.rapidapi.com/properties/v2/listapplication/jsond2fd74f727msh8259feea6125027p13558fjsnb70d55e8dca2hotels4.p.rapidapi.com").then((resp) =>  {
    //    console.log(resp);
    //   })
    // }
  },
  mounted() {
    this.fecthTomTom()
    // this.fetchsatel()
    
   
  
}
}
</script>
<style lang="">
  
</style>