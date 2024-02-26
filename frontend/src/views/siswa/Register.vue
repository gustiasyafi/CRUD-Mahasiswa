<template>
   <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <div class="container">
        <div class="navbar-brand">UAS Frontend</div>
  
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav mr-auto">
            <li class="nav-item">
              <router-link class="nav-link" :to="{ name: 'login' }"
                >Login</router-link
              >
            </li>
            <li class="nav-item">
              <router-link class="nav-link" :to="{ name: 'register' }"
                >Register</router-link
              >
            </li>
          </ul>
        </div>
      </div>
    </nav>
  <div class="container mt-5">
    <div class="row justify-content-center">
      <div class="col-md-6">
        <div class="card border-0 rounded shadow">
          <div class="card-body">
            <h2 class="text-center mb-4">Register</h2>

            <form @submit.prevent="saveData">
              <div class="form-group">
                <label for="name">First Name</label>
                <input
                  type="text"
                  v-model="siswa.name"
                  id="name"
                  class="form-control"
                  placeholder="Enter your first name"
                />
              </div>

              <div class="form-group">
                <label for="email">Email</label>
                <input
                  type="email"
                  v-model="siswa.email"
                  id="email"
                  class="form-control"
                  placeholder="Enter your email"
                />
              </div>

              <div class="form-group">
                <label for="password">Password</label>
                <input
                  type="password"
                  v-model="siswa.password"
                  id="password"
                  class="form-control"
                  placeholder="Enter your password"
                />
              </div>

              <button type="submit" class="btn btn-success btn-block">
                Register
              </button>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Register",
  data() {
    return {
      result: {},
      siswa: {
        name: "",
        email: "",
        password: "",
      },
    };
  },
  created() {},
  mounted() {
    console.log("mounted() called.......");
  },
  methods: {
    saveData() {
      axios
        .post("http://127.0.0.1:8000/api/register", this.siswa)
        .then(({ data }) => {
          console.log(data);
          try {
            alert("Registrasi telah berhasil dilakukan");
            this.$router.push({ name: "login" });
          } catch (err) {
            alert("failed");
          }
        });
    },
  },
};
</script>