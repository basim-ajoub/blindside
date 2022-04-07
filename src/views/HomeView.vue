<template>
  <div class="home">
    <h2>Blind Side Test</h2>
    <div class="login-comp">
      <h2>LogIn</h2>
      <div class="form-box">
        <h3>Email</h3>
        <input v-model="email" type="email" />
        <h3>Password</h3>
        <input v-model="password" type="password" />

        <button v-on:click="logIn" class="submit">LogIn</button>
        <p>"email": "basem2@blindside.com", "password": "123456",</p>
      </div>
    </div>
    <h2>Applicant's Name : Basim Ajoub</h2>
    <h2>FrameWork : Vue.js</h2>
  </div>
</template>

<script>
// @ is an alias to /src
import logindata from "../../db.json";
export default {
  name: "HomeView",
  data() {
    return {
      email: "",
      password: "",
      database: logindata,
    };
  },
  methods: {
    logIn() {
      let result = this.database;

      // this.$router.push({ name: "HomeUser" });
      let loginInfo = {
        email: this.email,
        password: this.password,
      };
      var emailDataBase = result.user[0].email;
      var passwordDataBase = result.user[0].password;
      if (
        emailDataBase == loginInfo.email &&
        passwordDataBase == loginInfo.password
      ) {
        localStorage.setItem("user-Info", JSON.stringify(loginInfo));
        this.$router.push({ name: "about" });
        window.alert("matched");
      } else {
        window.alert("Wrong Password or Email !");
      }

      window.alert(loginInfo.email);
    },
  },
};
</script>
<style lang="scss">
.home {
  width: 100%;
}
h2 {
  text-align: center;
}
.login-comp {
  width: 30%;
  height: 400px;
  margin-top: 70px;
  background: rgb(190, 187, 187);
  margin-left: 35%;
}
</style>
