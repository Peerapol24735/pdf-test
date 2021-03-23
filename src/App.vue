<template>
  <div id="app">
    <div class="text-center">
      <img alt="Vue logo" src="./assets/logo.png" />
      <HelloWorld msg="Welcome to Your Vue.js App" />
      <p>ผู้รับเงิน</p>
    </div>
    <button @click="generateReport">download</button>
    <div>
      <vue-html2pdf
        :show-layout="false"
        :float-layout="true"
        :enable-download="false"
        :preview-modal="true"
        :paginate-elements-by-height="1400"
        filename="hee hee"
        :pdf-quality="2"
        :manual-pagination="false"
        pdf-format="a4"
        pdf-orientation="portrait"
        pdf-content-width="800px"
        @progress="onProgress($event)"
        @hasStartedGeneration="hasStartedGeneration()"
        @hasGenerated="hasGenerated($event)"
        ref="test"
      >
        <section slot="pdf-content">
          <div class="text-center">
            <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
            <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
            <p>ผู้รับเงิน</p>
          </div>
        </section>
      </vue-html2pdf>
    </div>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import VueHtml2pdf from "vue-html2pdf";
export default {
  name: "App",
  components: {
    HelloWorld,
    VueHtml2pdf,
  },
  methods: {
    generateReport() {
      this.$refs.test.generatePdf();
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;500;600&display=swap");
* {
  font-family: Kanit, Helvetica, Arial, sans-serif;
}
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.text-center {
  text-align: center;
}
</style>
