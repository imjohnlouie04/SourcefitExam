<template>
  <div id="app">
    <header>
      <button :class="['menu-click', openMenu ? 'toggle' : '']" @click="openMenu = !openMenu">
        <span></span>
      </button>
      <div class="logo">
        <img src="@/assets/images/logo.svg" alt="">
      </div>
      <ul :class="[openMenu ? '' : 'hide']">
        <li v-for="(list, i) in navbar" :key="i"><a href="">{{ list }}</a></li>
      </ul>
      <div :class="['sidebar-bg',openMenu ? '' : 'hide']" @click="openMenu = !openMenu"></div>
    </header>
    <!-- hero banner -->
    <div class="hero">
      <div>
        <img src="@/assets/images/hero.png" alt="">
      </div>
      <div>
        <h1>Work Hard, drink harder</h1>
        <p>
          We may be <span class="info">drunk</span> but we deliver <span class="accent">quality</span> working websites and softwares
        </p>
        <ul>
          <li><i class="bullet"></i>Personal and corporate websites</li>
          <li><i class="bullet"></i>Customer relation management systems</li>
          <li><i class="bullet"></i>E-commerce website</li>
          <li><i class="bullet"></i>Software application as service systems</li>
        </ul>
        <button class="btn warning-btn request-quote">
          Request a quote
        </button>
      </div>
    </div>

    <!-- article -->
    <div class="header-title">Articles</div>
    <blog :articles="blogs" :articleToShow="blogToShow"></blog>
    <div @click="blogToShow += 3" class="link" style="text-align: center; cursor: pointer">Explore more articles</div>

    <!-- contact -->
    <contact></contact>

    <!-- signup -->
    <sign-up></sign-up>

    <!-- footer -->
    <footer>
      <div>© 2016-2019. Drunk Developers.All right reserved.</div>
      <div>Like us on <span class="info">Facebook</span></div>
      <div>Follow us on <span class="info">Twitter</span></div>
    </footer>
  </div>
</template>
<script>
const url = "https://jsonplaceholder.typicode.com/posts"
import axios from 'axios'
import blog from '@/views/article'
import contact from '@/views/contact'
import signUp from '@/views/signup'
export default {
  components: {
    blog,
    contact,
    signUp
  },
  data() {
    return {
      openMenu: false,
      navbar: [
        'Projects',
        'Testimonials',
        'Articles',
        'Contact Us'
      ],
      blogs: [],
      blogToShow: 3,
    }
  },
  methods: {

  },
  mounted () {
    axios
    .get(url)
    .then(response => {
      // console.log(response.data);
      this.blogs = response.data
    })
  },
  watch: {
    'this.blogToShow': function(n) {
      if (n) {
        this.blog
      }
    },
  }
}
</script>

<style>
@import 'assets/css/index.css'; 

#app {
  position: relative;
  background: url('assets/images/hero-bg.png');
  background-size: contain;
  background-repeat: no-repeat;
  margin: 0 auto;
  padding: 15px;
}


@media (min-width: 1024px) {
  #app {
    width: 960px;
    margin: 0 auto;
  }
}

/* Header */
header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  padding: 0 15px;
  height: 50px;
  background-color: #fff8db;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

header .sidebar-bg {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0,0,0,.5);
  opacity: 1;
  transition: opacity .3s;
  visibility: visible;
}

header .sidebar-bg.hide {
  opacity: 0;
  visibility: hidden;
}

header .menu-click {
  position: relative;
  width: 30px;
  height: 24px;
  background-color: transparent;
  border: 0;
  cursor: pointer;
  margin-right: 15px;
}

header .menu-click:after,
header .menu-click:before,
header .menu-click span {
  background: #5f656f;
}

header .menu-click:after,
header .menu-click:before {
  content: '';
  position: absolute;
  top: 50%;
  left: 0;
  width: 100%;
  height: 2px;
  pointer-events: none;
  transition: transform 0.25s;
  transform-origin: 50% 50%;
}

header .menu-click:after {
  transform: translate3d(0, -10px, 0) scale3d(0.8, 1, 1);
}

header .menu-click:before {
  transform: translate3d(0, 10px, 0) scale3d(0.8, 1, 1);
}

header .menu-click span {
  position: absolute;
  left: 0;
  overflow: hidden;
  width: 100%;
  height: 2px;
  text-indent: 200%;
  transition: opacity 0.25s;
}

header .logo {
  width: 100%;
  display: flex;
  justify-content: center;
}

header .logo img {
  width: 80%;
}

header ul {
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  z-index: 1;
  display: block;
  width: 220px;
  background-color: #fff;
  list-style: none;
  padding: 0;
  margin: 0;
  transform: translateX(0);
  transition: transform .3s;
}

header ul.hide {
  transform: translateX(-220px);
}

header ul li {
  padding: 0 10px;
}

header ul li a {
  color: #0F5C74;
  text-decoration: none;
  font-size: 20px;
}

@media (min-width: 1024px) {
  header {
    position: relative;
    background-color: transparent;
    height: auto;
    padding: 0;
  }

  header .logo {
    width: 400px;
  }

  header .sidebar-bg,
  header .menu-click {
    display: none;
  }

  header .sidebar-bg.hide,
  header ul.hide {
    transform: translateX(0);
  }

  header ul {
    position: relative;
    display: flex;
    z-index: 0;
    background-color: transparent;
    width: auto;
  }
}

/* hero */
.hero {
  display: flex;
  flex-flow: column;
  margin-top: 65px;
}

.hero div {
  width: 100%;
}

.hero div .request-quote {
  color: #fff;
  box-shadow: 0 5px 10px #febd89;
  margin: 40px auto 0;
}

.hero div h1 {
  margin-bottom: 0;
  font-size: 2.5em;
}

.hero div > p {
  margin-top: 5px;
  font-size: 16px;
  width: 350px
}

.hero div ul {
  list-style: none;
}

@media (min-width: 1024px) {
  .hero {
    flex-flow: row-reverse;
    margin-top: 15px;
  }

  .hero div {
    width: 50%;
  }

  .hero div h1 {
    font-size: 2em;
  }

  .hero div img {
    width: 100%;
  }
}

footer {
  margin-top: 40px;
  margin-left: -15px;
  margin-right: -15px;
  margin-bottom: -15px;
  padding: 15px;
  min-height: 200px;
  background-color: #6138d5;
  color: #fff;
  text-align: center;
  font-size: 1.5em;
  font-weight: bold;
}

footer div:nth-child(2) {
  margin-top: 80px;
}
</style>
