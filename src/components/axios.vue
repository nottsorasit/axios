<template >
  <div class="contrainer">
    <h1>Mars Rover Photos</h1>
    <h2>Querying by Earth date</h2>
    <br />
    <div class="row">
      <div class="col" v-for="(item, index) in httpdata.photos" :key="index">
        <div class="ee">
          <b-card v-bind:img-src="item.img_src" style="max-width: 500px">
            <h6>ID:</h6>
            {{ item.id }} <br />
            <h6>SOL:</h6>
            {{ item.sol }} <br />
            <h6>CAMERA:</h6>
            {{ item.camera }} <br />
            <h6>EARTH DATE:</h6>
            {{ item.earth_date }} <br />
            <h6>ROVER:</h6>
            {{ item.rover }} <br />
          </b-card>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return { httpdata: "" };
  },
  mounted() {
    axios({
      method: "GET",
      url:
        "https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?earth_date=2015-6-3&api_key=DEMO_KEY",
    }).then((result) => {
      this.httpdata = result.data;
    });
  },
};
</script>

 <style>
h1 {
  color: darkblue;
}

h6 {
  color: darkorange;
}
.col {
  color: darkviolet;
}
</style>