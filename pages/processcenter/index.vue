<template>
  <el-container style="height: 100vh; border: 1px solid #eee; display: block">
    <NavBar />
    <div class="mainprocess block">
      <el-timeline>
        <el-timeline-item
          v-for="(activity, index) in activities"
          :key="index"
          :icon="activity.icon"
          :type="activity.type"
          :color="activity.color"
          :size="activity.size"
          :timestamp="activity.timestamp"
        >
          {{ activity.content }}
        </el-timeline-item>
      </el-timeline>
    </div>
    <el-container style="justify-content: center; margin-top: 4vh">
      <el-upload action="#" list-type="picture-card" :auto-upload="false" v-model="form.image_url" >
        <i slot="default" class="el-icon-plus"></i>
        <div slot="file" slot-scope="{ file }">
          <img class="el-upload-list__item-thumbnail" :src="file.url" alt="" />
          <span class="el-upload-list__item-actions">
            <span
              class="el-upload-list__item-preview"
              @click="handlePictureCardPreview(file)"
            >
              <i class="el-icon-zoom-in"></i>
            </span>
            <span
              v-if="!disabled"
              class="el-upload-list__item-delete"
              @click="handleDownload(file)"
            >
              <i class="el-icon-download"></i>
            </span>
            <span
              v-if="!disabled"
              class="el-upload-list__item-delete"
              @click="handleRemove(file)"
            >
              <i class="el-icon-delete"></i>
            </span>
          </span>
        </div>
      </el-upload>
      <el-dialog :visible.sync="dialogVisible">
        <img width="100%" :src="dialogImageUrl" alt="" />
      </el-dialog>
      <el-button type="success" round style="height:40px; margin-top: auto;" 
        @click="fetchPerson()"
      >Success</el-button>
    </el-container>
  </el-container>
</template>
<style>
.mainImg {
  display: grid;
  justify-content: center;
  justify-items: center;
}
.mainprocess {
  margin-top: 4vh;
}
</style>
<script>
import NavBar from "../../components/NavBar.vue";
import axios from "axios";
import { createStore } from 'vuex'

const store = createStore({
  state () {
    return {
      newData: [[null]],
    }
  },
  mutations: {
    updateData(state, respo) {
      console.log("Updating data");
      state.newData = respo
    },
  },
})

export default {
  data() {
    return {
      activities: [
        {
          content: "Custom icon",
          timestamp: "2018-04-12 20:46",
          size: "large",
          type: "primary",
          icon: "el-icon-more",
        },
        {
          content: "Custom color",
          timestamp: "2018-04-03 20:46",
          color: "#0bbd87",
        },
        {
          content: "Custom size",
          timestamp: "2018-04-03 20:46",
          size: "large",
        },
        {
          content: "Default node",
          timestamp: "2018-04-03 20:46",
        },
      ],
      form: { username: '', 
      image_url: {} 
      },
      dialogImageUrl: "",
      dialogVisible: false,
      disabled: false,
      api: {},
    };
  },
  computed: {
    console: () => console,
  },
  created() {
    this.isloading = true;
    this.fetchPerson();
  },
  methods: {
    getUrl(file){
      this.fileImg = file.url
      this.console.log(this.fileImg)
    },

    handleRemove(file) {
      file.url = null;
    },
    handlePictureCardPreview(file) {
      this.dialogImageUrl = file.url;
      this.dialogVisible = true;
    },
    handleDownload(file) {
      document.execCommand("SaveAs", true, url);
    },
    increment() {
      store.commit('updateData')
    },


    async fetchPerson() {
        await axios({
          method: "post",
          url: "https://api.imgur.com/3/image",
          headers: {
            Authorization: `Client-ID ff80a62bfa31507`,
          },
          data: this.form.image_url,
        })
        .then(
          ({ data }) => (
            (this.api = data),
            this.$notify({
              title: "Success",
              message: "This is a success message",
              type: "success",
            })
          )
        )
        .catch((err) => {
          this.$notify.error({
            title: "Error",
            message: "This is an error message",
          });
        });
    },
  },

  components: { NavBar },
};
</script>
