<template>
  <el-container style="border: 1px solid #eee; display: block">
    <NavBar />
    <div>
      <el-row style="margin: 4vh 4vh; justify-content: space-between">
        <el-col
          :span="6"
          v-for="(result, i) in api.results"
          :key="i"
          :offset="url > 0 ? 4 : 0"
          style="padding: 4vh 4vh"
        >
          <el-card id="cards" class="justify-start ma-1">
            <el-card-text>
              <h1 class="mb-5">{{ result.name }}</h1>
              <p id="ptag">Population: {{ result.Population }}</p>
              <p id="ptag">surface_water: {{ result.surface_water }}</p>
              <p id="ptag">gravity: {{ result.gravity }}</p>
              <p id="ptag">climate: {{ result.climate }}</p>
            </el-card-text>
          </el-card>
        </el-col>
      </el-row>
      <!-- <Loader v-show="isloading" /> -->
      <Loader v-show="isloading" />
    </div>
  </el-container>
</template>

<script>
import axios from "axios";
import Loader from "../../components/Loader.vue";
export default {
  components: {
    Loader,
  },
  data() {
    return {
      api: {},
    };
  },
  created() {
    this.isloading = true;
    this.fetchPerson();
  },
  methods: {
    fetchPerson() {
      axios
        .get("https://swapi.dev/api/planets/")
        .then(
          ({ data }) => (
            (this.api = data), (this.isloading = false), console.log(data)
          )
        );
    },
    next() {
      this.fetchPerson(this.api.next);
    },
    previous() {
      this.fetchPerson(this.api.previous);
    },
  },
};
</script>
<style scoped>
#btn {
  position: absolute;

  bottom: 5px;
}
</style>
