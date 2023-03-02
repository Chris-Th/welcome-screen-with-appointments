<template>
  <!-- ===========================
  <img alt="Vue logo" src="./assets/logo.png">
  ============================ -->
  <HelloWorld msg=""/>
  
  <div id="app">
  
    <div class="container-fluid m-5 main-container">

      <div class="row  pb-3">
        <div class="col-sm-12">
          <h1 class="top-title pt-3">
            {{ title }}
          </h1>
          <h1 class="date py-2 mb-1">
            {{ currentDate }}
          </h1>
        </div>
      </div>
      <ul v-if="entries" class="entries-list" >
        <li  v-for="entry in entries" :key="entry.id">
          <div class="row pb-4 pt-2">
          
            <div class="col-sm-12">
              <div class="entry-item">
                <p class="item item-time">{{ entry[1] }} {{ entry[0] }} Uhr</p>
                <p class="item item-title">{{ entry[2] }}</p>
                <p class="item item-description">{{ entry[3] }}</p>
              </div>
            </div>
          </div>
        </li>
      </ul>

    <h1 v-else>Zur Zeit keine Events!</h1>

    </div>

    <nav class="navbar navbar-expand-sm fixed-bottom footer py-0">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">
          <img src="img/STZH_SEB_Logo.png" alt="Avatar Logo"  style="width: 230px;" class=""> 
        </a>
        <a class="navbar-brand" href="#">
          <img src="img/Opportunity.png" alt="Avatar Logo" style="width: 200px;" class=""> 
        </a>
        <a class="navbar-brand" href="#">
          <img src="img/SAG_Logo_De.png" alt="Avatar Logo" style="width: 200px;" class=""> 
        </a>
      </div>
    </nav>  

  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

// import { time } from 'console';

export default {
  name: 'App',
  data() {
    return {
      title:"Welcome to Opportunity",
      currentDate: "2.3.2023",
      entries: []
    };
  },
  methods: {
    getData() {
      this.entries = [ 
        // time, date, title, description
        ["8:25", "11/11/1111", "Feier", "failure"],
        ["17.25", "22/22/2222", "wedding", "of a paper clip"]
      ] 
    },

    
    updateCurrentDate() {
      let today = new Date();
      this.counter++;
      this.currentDate = `${today.getDate()}.${today.getMonth()}.${today.getFullYear()}`;
      this.currentTime = ``;

    },
    refreshData() {
      this.updateCurrentDate();
      this.getData();
    },
  },
  mounted() {
    this.refreshData(); // get first initial data then wait for the next
    setInterval(this.refreshData, 60000); // wait 1 min for next update
  },
};




  /*components: {
    HelloWorld
  }
};*/
</script>

<style>
     
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@500;900&display=swap%22");

 * {
   font-family: inter;
 }
 
 .main-container {
  font-family: inter;
  height: 1920px;
  width: 1080;
  background-color: #E8EFF4;
  padding-inline: 2.5rem;
  }


 .top-title {
   color: #323D4A;
   font-weight: 900;
   font-size: 62px;
   line-height: 75px;
   margin-bottom: 0.8rem;
 }

 .date {
   color: #9AA7B1;
   font-size: 62px;
   line-height: 72px;
   font-weight: 100;
   font-style: normal;
 }

 .item {
   
   font-size: 28px;
   line-height: 36px; 
   margin-bottom:0.1rem;
 }
 .entry-item {
   display: inline-block;
   background-color: #0F05A0;
   width: 100%;
   height:fit-content;
   margin: auto;
   padding-block: 2rem;
   padding-inline: 2rem;
 
 }
 .item-time {
   color: #EB5E00;
   font-weight: bold;
   padding:0;
 }
 .item-title {
   color: #FFBFAB;
   font-weight: bolder;
 }
 .item-description {
   color: #FFBFAB;
 }

 .footer {
   width: 100%;
   height: 130px;
   padding: 0.5rem;
   background-color: white;
 }

 .logo {
   height: 55px;
 }
</style>
