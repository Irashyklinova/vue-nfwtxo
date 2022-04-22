<template>
  <div id="app">
    <h2>Информация о пользователях</h2>
  </div>

  <div class="card" v-for="user in users">
    <img :src="user.picture.large" class="photo" alt="photo" />
    <div>
      {{ user.name.title }}.
      {{ user.name.first }}
      {{ user.name.last }}
    </div>
    <div>
      {{ user.dob.age }},
      {{ user.gender }}
    </div>
    <div>
      {{ user.location.country }},
      {{ user.location.city }}
    </div>
    <div>
      {{ user.phone }}
    </div>
    <a href="#">{{ user.email }}</a>
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {},

  data() {
    return {
      users: [],
    };
  },

  mounted() {
    fetch('https://randomuser.me/api/?results=10')
      .then((response) => {
        return response.json();
      })
      .then((data) => {
        console.log(data);
        this.users = data.results;
      });
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.card {
  margin-bottom: 25px;
}
.photo {
  border: 3px solid;
  border-radius: 15px;
}
</style>
