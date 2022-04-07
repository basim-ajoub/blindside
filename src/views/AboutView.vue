<template>
  <div class="about">
    <h1>This is an BlindSide Videos</h1>
    <p>{{ relatedvideos[0] }}</p>
    <HelloWorld
      class="onebox"
      v-for="project in projects"
      :key="project.id"
      :type="project.type"
      :imgSrc="project.imgsrc"
      :pstno="project.pstno"
      :commentpst="project.commentpst"
      :methods="relatedVideoFunc"
    />
    <div id="view-project-box" class="view-project-box">
      <button @click="closeProjectImage" class="close-btn">X</button>
      <div class="view-img">
        <iframe id="big-video" height="320px" width="700px"> </iframe>
      </div>
      <p id="view-type"></p>
      <div id="relatedvideo"></div>
    </div>
  </div>
</template>
<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import jsonProjects from "../../projects.json";
export default {
  name: "HomeView",
  components: {
    HelloWorld,
  },
  data: function () {
    return {
      projects: jsonProjects,
      relatedvideos: [],
    };
  },
  methods: {
    relatedVideoFunc: function () {
      var typeIp = document.getElementById("view-type").innerText;
      document.getElementById("relatedvideo").innerHTML = "";
      var no = this.projects.length;
      for (let i = 0; i <= no; i++) {
        if (this.projects[i].type == typeIp) {
          var x = this.projects[i].imgsrc;
          document.getElementById("relatedvideo").innerHTML +=
            '<iframe class="related-box" src="' + x + '"  > </iframe>';
        }
      }
    },
    closeProjectImage: function () {
      document.getElementById("view-project-box").style.display = "none";
    },
  },
};
</script>
<style lang="scss">
.onebox {
  float: left;
}
h1 {
  margin-left: 40%;
}
.view-project-box {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background: rgba(31, 29, 29, 0.836);
  display: none;
  .close-btn {
    position: absolute;
    width: 6.5%;
    right: 0%;
    &:hover {
      width: 7%;
    }
  }

  .view-img {
    width: 50%;
    height: 400px;
    margin-left: 23%;
    margin-top: 15px;

    img {
      height: 400px;
    }
  }
}
.related-box {
  margin-left: 2%;
}
</style>
