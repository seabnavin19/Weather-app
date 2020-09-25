<template>
  
  <div>
    <div class="form-inline my-2 m-5 col-6" >
      <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search" v-model="query">
      <button class="btn btn-outline-success" type="submit" @click="search">Search</button>
    </div>
    <div class="card col-6 m-5 pl-5 pt-5 pb-5 "  >
      <img src="../assets/clear.jpg" class="card-img-top h-50 w-100" alt="..." v-if="weather.main.temp-273>21">
      <img src="../assets/cloud.jpeg" class="card-img-top h-50 w-100" alt="..." v-if="weather.main.temp-273<=21">
  <div class="card-body">
    <h2 class="card-title">{{weather.name}}</h2>
    <h4 class="card-text">{{date}}</h4>
    <h5 class="card-text">{{ weather.weather[0].main }}</h5>
    <h5 class="card-text">{{ Math.round(weather.main.temp)-273 }}°c</h5>
  
  </div>
</div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";

export default {
  name: "Home",
  data () {
    return {
      query: "Phnom Penh",
      date:"",
      weather: {},
      apibaseurl:"http://api.openweathermap.org/data/2.5/"
    }
  },
  created(){
    this.getweter().then(res=>{
      this.weather=res.data
    }).catch(err=>console.error(err));
    this.getNow();
    this.query="";
  },
  methods:{
    search(){
      this.getweter().then(res=>{
      this.weather=res.data
    }).catch(err=>console.error(err));
    this.getNow();
    this.query="";
    },
    getweter(){
      return axios.get(this.apibaseurl+"weather?q="+this.query+"&?units=metric&APPID=0a0417bc4926b3a7ae35ad440f3fce22")
    },
    getNow: function() {
                    const today = new Date();
                    const date = today.getFullYear()+'-'+(today.getMonth()+1)+'-'+today.getDate();
                    const time = today.getHours() + ":" + today.getMinutes() + ":" + today.getSeconds();
                    const dateTime = date +' '+ time;
                    this.date = dateTime;
                }
    
  }
};

</script>
