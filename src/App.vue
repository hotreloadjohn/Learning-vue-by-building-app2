<template>
  <div id="app">
    <main>
      <div class="search-box">
        <input v-model="query" @click="clearResult" @keyup.enter="queryData" type="text" class="search-bar" placeholder="Search...">
      </div>
      
      <div class="weather-wrap">
        <div class="location-box">
          <div v-if="showResult" class="location"> {{location}} </div>
          <div v-if="showResult" class="date"> {{ date }}</div>
        </div>

        <div class="weather-box">
          <div v-if="showResult" class="weather">Rain</div>
          <div v-if="showResult" class="temp">33°C</div>
        </div>

      </div>

    </main>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      query: '',
      showResult: false,
      location: '',
      date: ''
    }
  },
  methods: {
    queryData() {
      // console.log(`make api ${this.query}`);
      this.showResult = true;
      this.location = this.query;
      this.date = new Date().toDateString();
      this.query = '';
      document.activeElement.blur();
    },
    clearResult() {
      this.showResult = false;
    }
  }
}
</script>

<style>

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'montserrat', sans-serif;
}

#app {
  background-image: url('./assets/sg-sky.jpg');
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}

main {
  min-height: 100vh;
  padding: 25px;
}

.search-box, .search-bar {
  display: block;
  width: 100%;
  padding: 15px;
  color: #313131;
  font-size: 20px;
  appearance: none;
  border:none;
  outline: none;
  background: none;
  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 0px 16px 0px 16px;
  transition: 0.4s;
}

.search-box .search-bar:focus {
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.75);
  border-radius: 16px 0px 16px 0px;
}

/* .location, .date, .temp, .weather {
  color: white;
} */

.location-box .location {
  color: #FFF;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}

.location-box .date {
  color: #FFF;
  font-size: 20px;
  font-weight: 300;
  font-style: italic;
  text-align: center;
}
.weather-box {
  text-align: center;
}
.weather-box .weather, .temp {
  display: inline-block;
  padding: 10px 25px;
  color: #FFF;
  font-size: 102px;
  font-weight: 900;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  background-color:rgba(255, 255, 255, 0.25);
  border-radius: 16px;
  margin: 30px 0px;
  box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}

.weather-box .temp {
  margin-left: 10%;
}
/* .weather-box {
  display: flex;
  flex-wrap: nowrap;
} */

</style>
