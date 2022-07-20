<template>
  <div class="container">
    <Header />
    <div class="card mt-5">
      <div class="row gx-3 p-2">
        <div class="col-md-5">
          <img src="@/assets/images/cardMedia/large.png" class="img-fluid w-100 h-100" alt="...">
        </div>
        <div class="col-md-7 position-relative">
          <p>Front End <small class="text-muted">-1 Hour Ago</small></p>
          <h5>Optimizing CSS for faster page loads </h5>
          <p class="text-secondary">Not long ago I decided to improve the loading times of my website. It already
            loads pretty
            fast, but I
            knew there was still room for improvement and one of them was CSS loading. I will walk you through the
            process and show you how you can improve your load times as well.</p>
          <p class="text-secondary">
            To see how CSS affects the load time of a webpage we first have to know how the browser converts an HTML
            document into a functional webpage...</p>
          <div class="w-100 position-absolute d-flex justify-content-between bottom">
            <p class="card-text"><small class="text-muted"> 3 mins Read</small></p>
           <router-link :to="'/details'">
           <p class="card-text text-primard">
            <small>Full Read</small>
              <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
                class="bi bi-arrow-right" viewBox="0 0 16 16">
                <path fill-rule="evenodd"
                  d="M1 8a.5.5 0 0 1 .5-.5h11.793l-3.147-3.146a.5.5 0 0 1 .708-.708l4 4a.5.5 0 0 1 0 .708l-4 4a.5.5 0 0 1-.708-.708L13.293 8.5H1.5A.5.5 0 0 1 1 8z" />
              </svg>
            </p>
</router-link>

           

          </div>
        </div>
      </div>
    </div>
    <!-- cards -->
    <section class="mt-5">
      <div class="d-flex justify-content-between flex-wrap">
        <!-- created an array to get all the available posts in the url  -->
        <!-- post is any name u chose to name your objects -->
        <!-- assign a unique key value e.g post.id -->
        <BlogCard v-for="post in posts" :key="post.id" :post="post"/>
      </div>
    </section>
    <section class="container mt-5">
      <Footer />

    </section>
  </div>
</template>

<script>
import Header from '@/components/header.vue'
import Footer from '@/components/footer.vue'
import BlogCard from '@/components/BlogCard.vue'
export default {
name: 'Home-Page',
  components: {
    Header,
    Footer,
    BlogCard
  },
  data() {
    //created a data name (posts) with an empty array  containing all data from our url
    // you can also set names and their values here if u want to
    return {
      posts: [],
      name: "irene"
    }
  },
  //all our fuctions 
  methods: {
    // fetch(url, headers, data)
    /* getPostUsingPromise() {
      fetch('https://techcrunch.com/wp-json/wp/v2/posts')
        .then(async (response) => {
          console.log(response);
          if (response.ok) {
            const data = await response.json();
            console.log(data)
          }
        })
        .catch((error) => {
          console.log(error)
        })
    }, */
    //created a fuction to fetch data from the backend
    // used fetch to get our data from the backend
    // catch method to throw an error if the fetch doesn't work
    getBlogPost() {
      fetch("https://techcrunch.com/wp-json/wp/v2/posts")
        .then(async (response) => {
          if (response.ok) {
            // call all objects in the url 
            this.posts = await response.json()
          }
        })
        .catch((err) => {
          console.log(err)
        })
    }
  },
  computed: {

  },
  //vue life circle 
  created() {
    // call the function after creating it by using the THIS keyword
    // console.log("created hooks", this)
    // this.getPostUsingPromise()
    this.getBlogPost()
  },
  beforeMount() {
    console.log("beforemounting hooks", this)
  },
  mounted() {
    // console.log("mounted hooks", this)

  },
  beforeUnmount() {
    console.log("beforeUnmounted hooks", this)
  },
  unmounted() {
    console.log("unmounted hooks", this)
  },
  beforeCreate() {
    console.log("before created hooks", this)
  },
  beforeUpdate() {
    console.log("beforeupdate hooks", this)
  },

  updated() {
    console.log("updated hooks", this)
  },
}

</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

nav {
  display: flex;
  justify-content: space-between;
  /* background-color: aquamarine; */
}

.logo {
  margin-right: 5px;
}

.logo1 {
  margin: 5px 5px 5px 5px;
}

nav ul {
  display: flex;
  justify-content: flex-end;
  gap: 25px;
  align-items: center;
  text-align: center;
}

li {
  text-decoration: none;
  list-style: none;
}

.cardflex {
  display: flex;
  justify-content: space-between;
}

.bottom {
  bottom: 0
}

.box-card {
  display: flex;
  /* justify-content: space-between; */
  align-items: center;
}

.container1 {
  padding: 3rem 10rem;
}

footer {
  text-align: center;
  max-width: 40ch;
  margin: auto;
  line-height: 25px;

}
</style>
