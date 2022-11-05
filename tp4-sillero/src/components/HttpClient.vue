<template>

  <section class="src-componentes-http-client">
    <div class="jumbotron">
      <h2>Busqueda de Usuarios</h2>
      <br>

      <button class="btn btn-outline-dark my-3 mr-3" @click="getPostsXHRPromise()">XMLHttpRequest</button>
      <button class="btn btn-outline-dark my-3 mr-3" @click="getPostsFetch()">Fetch</button>
      <button class="btn btn-outline-dark my-3 mr-3" @click="getPostsAxios()">Axios</button>
      <button class="btn btn-danger my-3 mr-3" @click="posts= []">Clear</button>
      <br>

      <div v-if="posts.length" class="table-responsive">
        <table class="table table-light">
          <tr class="titulos">
            <th>Nombre</th>
            <th>Email</th>
            <th>Telefono</th>
          </tr>

          <tr v-for="post in posts" :key="post.id">
            <td>{{ post.nombre }}</td>
            <td>{{ post.email }}</td>
            <td>{{ post.telefono }}</td>
          </tr>
        </table>
      </div>
      <h4 v-else class="alert alert-warning text-center">Elegi un metodo de busqueda!</h4>
      
    </div>
  </section>

</template>

<script>

  export default  {
    name: 'src-componentes-http-client',
    props: [],
    mounted () {

    },
    data () {
      return {
        url: 'https://633f79d2e44b83bc73bae575.mockapi.io/posts',
        posts : []
      }
    },
    methods: {
      xhrPromise() {
        return new Promise((resolve, reject) => {
          const xhr = new XMLHttpRequest()
         xhr.open('get', this.url)
         xhr.addEventListener('load', () => {
           if(xhr.status == 200) {
             let respuesta = JSON.parse(xhr.response)
            resolve(respuesta)
           }
           else {
            reject(xhr.status)
           }
         })
         xhr.send()
        })
      },

      async getPostsXHRPromise() {
        try {
          let respuesta = await this.xhrPromise()
          this.posts = respuesta
        } catch(error){
          console.error(error)
        }
      },

      async getPostsFetch(){
        
       try {
         let response = await fetch(this.url)
         let respuesta = await response.json()
         this.posts = respuesta

       } catch(error){
        console.error(error)
       }

      },

      async getPostsAxios(){
       try {
         let respuesta = await this.axios(this.url)
         this.posts = respuesta.data
       } catch(error) {
        error => console.error(error)
       }
      }
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .titulos th {
    color: #f5a0a8;
  }

  .jumbotron {
    background-color: #f8bdc2;
    color: white;
    font-family: 'Fira Sans', sans-serif;
  }

  hr {
    background-color: #fff;
  }

</style>
