<template>
  <div id="app">
    <Notify :type="type" :message="message" :title="title" />
    <!-- all the page/views will be rendered here -->
    <router-view />
  </div>
</template>

<script>
import "./styles/default.scss";
import Notify from "@/components/Notify.vue";
export default {
  beforeCreate() {},
  data() {
    return {
      title: "",
      message: "",
      type: "",
    };
  },
  methods: {
    showLog(data) {
      this.type = data.type;
      this.message = data.message;
      this.title = data.title;
      setTimeout(() => {
        this.type = "";
        this.message = "";
        this.title = "";
      }, 4000);
    },
  },
  provide() {
    return {
      showLog: this.showLog,
    };
  },
  components: {
    Notify,
  },
};
</script>

<style lang="scss"></style>
