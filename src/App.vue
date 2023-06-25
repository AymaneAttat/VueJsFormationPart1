<template>
  <Header />
  <div class="container">
    <div class="text-center"><img alt="Vue logo" src="./assets/logo.png"></div>
    <div class="row">
      <div class="col-md-6 mx-auto text-center">
        <h1> {{message}} </h1>
        <!-- <AddCourse /> -->
      </div>
    </div>
    <Courses>
      <ol class="breadcrumb">
        <li class="breadcrumb-item"><a href="#">Home</a></li>
        <li class="breadcrumb-item active" aria-current="page">List Courses</li>
      </ol>
      <!-- <template v-slot:button-right>
        <button class="btn btn-sm btn-success">New</button>
      </template> -->
    </Courses>
  </div>
  <Footer url="https://brightcoding.dev" title="Bright Coding Certif" text="Check Your Certif" />
</template>

<script>
import Header from './components/Header.vue'
//import AddCourse from './components/AddCourse.vue'
import Courses from './components/Courses.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Header,
    //AddCourse,
    Courses,
    Footer
  },
  data () {
    return {
      message: 'Bright Coding'
    }
  },
  methods: {
    handleClick () {
      console.log(this.$refs.book.value)
      this.$refs.book.classList.add('active')
      this.$refs.book.focus()
    }
  }
}
</script>

<style>
/*#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}*/
.container {
  margin-top: 60px;
}
/*h1 {
  color: blue;
}*/
</style>
