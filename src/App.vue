<template>
  <section>
    <div class="container" v-if="user">
      <h1 class="heading">Olunu Abiodun</h1>

      <div class="image">
        <img
        src="@/assets/woman.png"
          alt="woman holding orange"
        />
      </div>
      <nav>
        <ul>
          <li><a href="#">Home</a></li>
          <li><a href="#">About</a></li>
          <li>
            <a href="#"><img src="@/assets/image.jpg" alt="image" /></a>
          </li>
          <li><a href="#">Gallery</a></li>
          <li><a href="#">Contact</a></li>
        </ul>
      </nav>

      <ul class="socials">
        <li>
          <a :href="`https://twitter.com/${user.social_media.twitter}`"
            ><i class="fab fa-twitter-square"></i
          ></a>
        </li>
        <li>
          <a :href="`https://instagram.com/${user.social_media.instagram}`"
            ><i class="fab fa-instagram"></i
          ></a>
        </li>
        <li>
          <a :href="`https://snapchat.com/${user.social_media.snapchat}`"
            ><i class="fab fa-snapchat-square"></i
          ></a>
        </li>
        <li>
          <a :href="`mailto:${user.social_media.email}`"
            ><i class="fas fa-envelope-square"></i
          ></a>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
import { ref } from "vue";
export default {
  name: "App",
  components: {},
  setup() {
    let user = ref(null);
    fetch("https://hirng-x2021.glitch.me/api")
      .then((res) => res.json())
      .then((data) => {
        console.log(data);
        user.value = data;
      });

    return { user };
  },
};
</script>






<style>
@import url(https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.1/css/all.min.css);
#app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  text-transform: uppercase;
  color: #fff;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

ul,
li {
  list-style: none;
}

a {
  text-decoration: none;
  color: inherit;
  cursor: pointer;
}

section {
  background-image: linear-gradient(to right, #bd0f4d 50%, #cb2964 50%);
  color: #fff;
  padding: 0 2rem;
}

section .container {
  max-width: 1440px;
  margin: auto;
  padding: 20px 0;
  height: 100vh;
  display: grid;
  grid-template-rows: auto 1fr auto;
  align-content: center;
  align-items: center;
  justify-content: center;
  gap: 30px;
  font-weight: 300;
  position: relative;
}

h1.heading {
  font-weight: 300;
  font-size: 40px;
  word-spacing: 1em;
}

div.image {
  background: #cb2964;
  width: 100%;
  box-shadow: 0px 0px 20px -10px #000;
}

.image img {
  width: 100%;
  display: block;
}

nav {
  display: flex;
  justify-content: center;
}

nav ul {
  display: grid;
  grid-template-columns: repeat(5, 120px);
  align-items: center;
  gap: 1em;
  font-size: 24px;
  text-transform: uppercase;
}

nav ul a {
  text-decoration: none;
  color: inherit;
}

nav ul li a img {
  border-radius: 50%;
  height: 70px;
  width: 70px;
  object-fit: cover;
  object-position: top;
}

.socials {
  display: flex;
  flex-direction: column;
  position: absolute;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

a {
  font-size: 32px;
}
</style>
