<template>
  <div class="about">
    <h1>This is an about page</h1>
    <button @click="getscore">GET</button>
  </div>
</template>
<script>
export default {
  name:"About",
  data(){
    return{
      score:[]
    }
  },
  methods:{
    getscore(){
      const axios = require("axios");

axios({
    "method":"GET",
    "url":"https://covid-19-data.p.rapidapi.com/report/country/name",
    "headers":{
    "content-type":"application/octet-stream",
    "x-rapidapi-host":"covid-19-data.p.rapidapi.com",
    "x-rapidapi-key":"be62b1ce4cmsh71db36992599e1bp12f3dejsne72029506de9",
    "useQueryString":true
    },"params":{
    "date-format":"YYYY-MM-DD",
    "format":"json",
    "date":"2020-04-01",
    "name":"Cambodia"
    }
    })
    .then((response)=>{
      console.log(response.data)
    })
    .catch((error)=>{
      console.log(error)
    })

    }
  }
}
</script>