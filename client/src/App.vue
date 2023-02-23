<script>

import axios from 'axios'

export default {
  name: "App",
  data() {
    return {
      setup: "",
      punchline: ""
    };
  },

  methods: {
    async getJoke() {
      let { data } = await axios.get("https://official-joke-api.appspot.com/random_joke")
      this.setup = data.setup
      this.punchline = data.punchline
    }

  },
  created() {
    this.getJoke()
  }
}



</script>




<template>
  <section class="bg-white shadow-sm">
    <div class="container">
      <h1 class="py-3 text-center">The Bapack-Bapack Joke</h1>
    </div>
  </section>

  <div class="container">
    <div class="row justify-content-center mt-5">
      <div class="col-md-6">
        <div class="card">
          <div class="card-body">
            <h5 class="card-title">{{ this.setup }}</h5>
            <p class="card-text">{{ this.punchline }} 😹</p>
            <br />
            <div>
              <button @click="getJoke" type="button" class="btn btn-danger ">Reload 💫</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
body {
  background-color: #F1E3D3;
}

.card {
  border-radius: 20px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
}
</style>