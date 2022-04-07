<template>
  <div class="hello">
    <div class="project-comp box">
      <div class="vedio-box">
        <iframe :src="this.imgSrc"> </iframe>
      </div>
      <div class="discrptions dis-box">
        <p class="disc-p">{{ type }}</p>
        <button @click="commentToggleOff" id="off-comment">Off Comm</button>
        <button @click="commentToggleOn" id="on-comment">On Comm</button>

        <ul :id="pstno" class="comment-window">
          <li>first coment</li>
          <li>second coment</li>
          <li>third coment</li>
        </ul>
        <input
          v-model="newcomment"
          placeholder="Add Comment"
          type="text"
          :id="commentpst"
        /><button @click="addComment">Add</button>
      </div>
    </div>
    <button @click="viewProjectVedieo" :class="'ptnViewDetails' + pstNo">
      <p>View</p>
    </button>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: ["type", "imgSrc", "pstno", "commentpst", "methods"],
  data() {
    return {
      newcomment: "",
    };
  },
  methods: {
    commentToggleOff: function () {
      document.getElementById(this.pstno).style.display = "none";
    },
    commentToggleOn: function () {
      document.getElementById(this.pstno).style.display = "block";
    },
    viewProjectVedieo: function () {
      document.getElementById("view-project-box").style.display = "block";
      document.getElementById("big-video").src = this.imgSrc;
      document.getElementById("view-type").innerText = this.type;

      this.methods();
    },
    addComment: function () {
      document.getElementById(this.pstno).innerHTML +=
        "<li>" + this.newcomment + "</li>";
      //to clear input comment
      document.getElementById(this.commentpst).value = " ";
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
.hello {
  background: rgba(131, 128, 128, 0.267);
  margin-left: 15px;
  margin-bottom: 50px;
}
.comment-window {
  list-style-type: none;
  max-height: 50rem;
  width: 100%;
  display: flex;
  flex-direction: column;
  li {
    width: 99%;
    margin-left: 0;
    max-height: 50px;
    overflow: auto;
    margin-bottom: 2px;
    border: 0.5px solid black;
  }
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
