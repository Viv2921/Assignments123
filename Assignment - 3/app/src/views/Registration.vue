<template>
  <div>
    <header>
      <div id="header">
        <img src="./asu logo.webp" alt="" id="logo" style="height: 72px" />
        <h1 id="career">CareerCatalyst</h1>
      </div>
      <div id="routes">
        <router-link to="/" id="link">Home </router-link> &nbsp;

        <router-link to="/contactus" id="link"> Contact Us </router-link>
        &nbsp;

        <router-link to="/courses" id="link"> Courses</router-link> &nbsp;
      </div>
    </header>

    <form action="reg2.html">
      <div class="formContainer">
        <h1>Sign Up Form</h1>
        <hr />
        <label for="username"><b>Username</b></label>
        <input
          type="text"
          placeholder="Enter username"
          name="username"
          required
          autocomplete="off"
          id="username"
        />
        <label for="email"><b>Email</b></label>
        <input
          type="email"
          placeholder="Enter Email"
          name="email"
          required
          autocomplete="off"
          id="email"
        />
        <label for="password"><b>Password</b></label>
        <input
          type="password"
          placeholder="Password"
          name="password"
          required
          autocomplete="off"
          id="password"
        />
        <label>
          <input
            type="checkbox"
            checked="checked"
            name="remember"
            style="margin-bottom: 15px"
          />
          Remember me
        </label>
        <p>
          Already a user
          <a href="login.html" style="color: dodgerblue">Login</a>
        </p>
        <p></p>
        <p>
          By creating an account you agree to our
          <a href="#" style="color: dodgerblue">Terms & Privacy</a>
        </p>
        <p></p>
        <div>
          <button type="button" class="cancel">Cancel</button>
          <button
            type="submit"
            class="signup"
            @click="saveData()"
            id="save_btn"
          >
            Sign Up
          </button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  methods: {
    saveData() {
      let username, email, password;
      username = document.getElementById("username").value;
      email = document.getElementById("email").value;
      password = document.getElementById("password").value;

      let user_records = new Array();
      if ("users" in localStorage) {
        user_records = JSON.parse(localStorage.getItem("users"));
      } else {
        user_records = [];
      }
      //?
      let data1 = { username: username, email: email, password: password };
      console.log(data1);
      user_records.push(data1);
      //localStorage.setItem("users", JSON.stringify(user_records));

      let xhr = new XMLHttpRequest();
      xhr.open("POST", "http://localhost:1500/users");
      xhr.setRequestHeader("Accept", "application/json");
      xhr.setRequestHeader("Content-Type", "application/json");
      // xhr.send();

      console.log(data1);
      xhr.onreadystatechange = () => {
        if (xhr.readyState === 4 && xhr.status === 200) {
          //  document.write(xhr.response);
        }
      };
      xhr.send(JSON.stringify(data1));

      // xhr.onreadystatechange=()=>{
      /* if(xhr.readyState === 4 && xhr.status === 200){
            document.write(xhr.response);
         } */
      document.write("registration successful please login");
    },
  },
};

//}
</script>

<style>
body {
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

* {
  box-sizing: border-box;
}

input[type="text"],
input[type="email"] {
  width: 100%;
  font-size: 28px;
  padding: 15px;
  margin: 5px 0 22px 0;
  display: inline-block;
  border: none;
  background: #f1f1f1;
}

input[type="text"],
input[type="password"] {
  width: 100%;
  font-size: 28px;
  padding: 15px;
  margin: 5px 0 22px 0;
  display: inline-block;
  border: none;
  background: #f1f1f1;
}

label {
  font-size: 15px;
}

input[type="text"]:focus,
input[type="email"]:focus {
  background-color: #ddd;
  outline: none;
}

input[type="text"]:focus,
input[type="password"]:focus {
  background-color: #ddd;
  outline: none;
}

hr {
  border: 1px solid #f1f1f1;
  margin-bottom: 25px;
}

button {
  font-size: 18px;
  font-weight: bold;
  background-color: rgb(10, 119, 13);
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  cursor: pointer;
  width: 100%;
  opacity: 0.9;
}

button:hover {
  opacity: 1;
}

.cancel {
  padding: 14px 20px;
  background-color: #ff3d2f;
}

.formContainer {
  padding: 16px;
}

.formContainer p {
  font-size: 28px;
}
#header {
  padding: 20px;
  width: 100%;
  border: 1px solid grey;
  border-left: none;
  border-right: none;
  border-top: none;
  height: 125px;
}
#career {
  margin-top: -78px;
  margin-right: 840px;
  font-size: 36px;
  font-weight: 700;
}
#logo {
  margin-left: -1200px;
}
#link {
  color: black;
  text-decoration: none;
}

#link:hover {
  text-decoration: 3px underline darkgoldenrod;
}

#career:hover {
  text-decoration: underline;
  cursor: pointer;
}
</style>
