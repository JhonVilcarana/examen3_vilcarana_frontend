<template>
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title>Contact Form Template</title>
    <link
      rel="stylesheet"
      href="/build/tailwind.css"
      type="text/css"
      media="screen"
      title="no title"
      charset="utf-8"
    />
  </head>
  <body>
    <div class="wrapper w-screen h-screen flex justify-center items-center bg-cover bg-center " style="background-image:url('https://i.ibb.co/4gq4M7R/UPe-U-campus-Lima-Ceremonia-de-graduacio-n-de-la-promocio-n-2019-Harry-Bill-Lunquist-4-1500x750.jpg') ">
      <div class="lg:w-1/2 xl:max-w-screen-sm">
        <div
          class="
            py-12
            flex
            justify-center
            lg:justify-start
            lg:px-12
          "
        >
          <div class="cursor-pointer flex items-center">
            <div>
              <img
                src="https://i.ibb.co/PC8SbXc/logo-upeu-white.png"
                alt="upeu-removebg-preview"
                border="0"
                width="500px"
              />
            </div>
            <div
              class="text-2xl text-red-800 tracking-wide ml-2 font-semibold"
            ></div>
          </div>
        </div>
        <div
          class="
            mt-10
            px-12
            sm:px-24
            md:px-48
            lg:px-12
            lg:mt-16
            xl:px-24
            xl:max-w-2xl
          "
        >
          <h2
            class="
              text-center text-4xl text-red-100
              font-display font-semibold
              lg:text-left
              xl:text-5xl xl:text-bold
    
            "
          >
            Iniciar Sesión
          </h2>
          <div class="mt-12">
            <form>
              <div>
                <div class="text-sm font-bold text-gray-50 tracking-wide">
                  Usuario
                </div>
                <input id="login" name="login"
                  class="
                    w-full
                    text-lg
                    py-2
                    px-4
                    border-b border-gray-300
                    focus:outline-none
                    focus:border-indigo-500
                    rounded-full
                  "
                  type="text"
                  placeholder="Ingresa tu usuario"
                />
              </div>
              <div class="mt-8">
                <div class="flex justify-between items-center">
                  <div class="text-sm font-bold text-gray-50 tracking-wide">
                    Contraseña
                  </div>
                  <div>
                    <a id="password" name="login"
                      class="
                        text-xs
                        font-display font-semibold
                        text-red-700
                        hover:text-indigo-800
                        cursor-pointer
                      "
                    >
                      Olvidaste tu contraseña?
                    </a>
                  </div>
                </div>
                <input
                  class="
                    w-full
                    text-lg
                    py-2
                    px-4
                    border-b border-gray-300
                    focus:outline-none
                    focus:border-indigo-500
                    rounded-full
                  "
                  type="password"
                  placeholder="Ingresa tu contraseña"
                />
              </div>
              <div class="mt-10">
                <button
                  class="
                    bg-gradient-to-r
                    from-purple-400
                    via-pink-500
                    to-red-500
                    text-gray-100
                    p-4
                    w-full
                    rounded-full
                    tracking-wide
                    font-semibold font-display
                    focus:outline-none
                    focus:shadow-outline
                    hover:bg-red-600
                    shadow-lg
                  "
                >
                  Iniciar Sesión
                </button>
              </div>
            </form>
            <div
              class="
                mt-12
                text-sm
                font-display font-semibold
                text-red-800 text-center
              "
            >
              No tienes una cuenta?
              <a class="cursor-pointer text-red-600 hover:text-red-800"
                >Registrate</a
              >
            </div>
          </div>
        </div>
      </div>
    </div>
  </body>
</template>
<script>
import axios from 'axios';
export default {
  name: 'Login',
  components: {
  },
  data: function(){
    return {
      usuario: "jhon",
      password: "123",
      error: false,
      error_msg: "",
    }
  },
  methods:{
    login(){
        let json = {
          "usuario" : this.usuario,
          "password": this.password
        };
        axios.post('http://solodata.es/auth', json)
        .then( data =>{
           if(data.data.status == "ok"){
             localStorage.token = data.data.result.token;
             this.$router.push('dashboard');
           }else{
             this.error = true;
             this.error_msg = data.data.result.error_msg;
           }
        })
    }
  }
}
</script>
<style scoped>
.st0 {
  fill: none;
  stroke: currentColor;
  stroke-width: 20;
  stroke-linecap: round;
  stroke-miterlimit: 3;
}
</style>