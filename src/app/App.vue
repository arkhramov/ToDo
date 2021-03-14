<template>
    <div class="wrapper">
      <header>
        <div class="header-img">
          <div class="container-fluid">
            <div class="center logo col-lg-12">ToDo Vue</div>
          </div>
        </div>
      </header>
      <nav class="navbar navbar-light bg-light" style="margin-bottom: 60px;">
        <div class="container-fluid">
          <a class="navbar-brand">ToDo Vue</a>
          <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
          <div class="navbar-nav">
          <a class="nav-link">Главная</a>
          <a class="nav-link">Пункт 1</a>
          <a class="nav-link">Пункт 2</a>
          <form class="d-flex">
            <a>Авторизация</a>
          </form>
          </div>
          </div>
        </div>
      </nav>
        <div class="container">
            <div class="row">
                <div class="col-sm-12">
                    <div v-if="alert.message" :class="`alert ${alert.type}`">{{alert.message}}</div>
                    <router-view></router-view>
                </div>
            </div>
        </div>
      <footer>
        <div style="padding: 30px;text-align: center">Copyright 2021</div>
      </footer>
    </div>
</template>

<script>
import { mapState, mapActions } from 'vuex'

export default {
    name: 'app',
    computed: {
        ...mapState({
            alert: state => state.alert
        })
    },
    methods: {
        ...mapActions({
            clearAlert: 'alert/clear'
        })
    },
    watch: {
        $route (to, from){
            // clear alert on location change
            this.clearAlert();
        }
    }
};
</script>

<style scoped>

footer {
  background: #ccc;
  margin-top:60px;
}

.header-img {
  display: block;
  height: 130px;
  background: url(https://images.unsplash.com/photo-1557682250-33bd709cbe85?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=1915&q=80) repeat-x center bottom;
}

.center { text-align: center;}

.logo { font-size: 64px; font-style: italic; color: #fff;  }


</style>
