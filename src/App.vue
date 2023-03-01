<template>
  <div class="container">
    <div>
      <h1>villa itria</h1>
      <div class="row g-4">
        <div class="col-2">
          <img class="img-fluid" src="https://a0.muscache.com/im/pictures/25af7fb2-36a6-4446-a2dc-3a6f9710e63c.jpg?im_w=1200" alt="">
        </div>
        <div class="col-2">
          <img class="img-fluid" src="https://a0.muscache.com/im/pictures/8fe5cd96-74cc-49a5-b2af-9ff5455ac7c4.jpg?im_w=720" alt="">
        </div>
        <div class="col-2">
          <img class="img-fluid" src="https://a0.muscache.com/im/pictures/207e21af-c211-4580-8487-973a1bc711e5.jpg?im_w=1200" alt="">
        </div>
        <div class="col-2">
          <img class="img-fluid" src="https://a0.muscache.com/im/pictures/d68a1a84-7b3a-4c06-85bf-09f9da92a34b.jpg?im_w=1200" alt="">
        </div>
        <div class="col-2">
          <img class="img-fluid" src="https://a0.muscache.com/im/pictures/75fd1d3a-2d64-4d43-8597-455eea00595b.jpg?im_w=720" alt="">
        </div>
        <div class="col-2">
          <img class="img-fluid" src="https://a0.muscache.com/im/pictures/e125d8ce-f33a-4db9-9cc9-907603cb72dd.jpg?im_w=720" alt="">
        </div>
        <div class="col-2">
          <img class="img-fluid" src="https://a0.muscache.com/im/pictures/38f721dc-7bb7-46b2-b023-230f0c151f1b.jpg?im_w=1440" alt="">
        </div>
        
      </div>
    </div>
    
    
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

    fetchsatel() {
      axios.post("https://hotels4.p.rapidapi.com/properties/v2/listapplication/jsond2fd74f727msh8259feea6125027p13558fjsnb70d55e8dca2hotels4.p.rapidapi.com").then((resp) =>  {
       console.log(resp);
      })
    }
  },
  mounted() {
    this.fecthTomTom(),
    this.fetchsatel()
  },
  
}
</script>
<style lang="">
  
</style>