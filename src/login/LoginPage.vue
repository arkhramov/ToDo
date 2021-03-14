<template>
    <div>
      <div class="col-sm-6" style="float: left">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean faucibus mauris enim, et ultrices mauris dignissim vel. Pellentesque ac tempus magna. Aliquam malesuada ligula sed mauris placerat ultrices. Cras sit amet nibh at erat auctor elementum at eget ex. Pellentesque eget mauris sit amet quam eleifend varius sit amet at libero. Proin eleifend tortor a est consequat lobortis. Ut bibendum justo quam, laoreet elementum tortor ullamcorper vitae. Phasellus pharetra vel velit non convallis. Nam rhoncus sapien sit amet nisi semper, vitae luctus velit cursus. Pellentesque vel bibendum dui. Aenean et est posuere, consectetur nulla eget, fringilla diam. Duis luctus erat urna, non lobortis mauris dictum non. Integer laoreet finibus dolor id venenatis. Integer ut consectetur quam. Donec mollis felis nec ligula dictum placerat quis a sapien. Nullam ut eleifend nisl, ut aliquam diam.
      </div>
      <div class="col-sm-6" style="float: left">
        <h2>Авторизация</h2>
        <form @submit.prevent="handleSubmit">
            <div class="form-group">
                <label for="username">Логин</label>
                <input type="text" v-model="username" name="username" class="form-control" :class="{ 'is-invalid': submitted && !username }" />
                <div v-show="submitted && !username" class="invalid-feedback">Логин неверный</div>
            </div>
            <div class="form-group">
                <label htmlFor="password">Пароль</label>
                <input type="password" v-model="password" name="password" class="form-control" :class="{ 'is-invalid': submitted && !password }" />
                <div v-show="submitted && !password" class="invalid-feedback">Пароль неверный</div>
            </div>
            <div class="form-group">
                <button class="btn btn-primary" :disabled="status.loggingIn">Войти</button>
                <img v-show="status.loggingIn" src="data:image/gif;base64,R0lGODlhEAAQAPIAAP///wAAAMLCwkJCQgAAAGJiYoKCgpKSkiH/C05FVFNDQVBFMi4wAwEAAAAh/hpDcmVhdGVkIHdpdGggYWpheGxvYWQuaW5mbwAh+QQJCgAAACwAAAAAEAAQAAADMwi63P4wyklrE2MIOggZnAdOmGYJRbExwroUmcG2LmDEwnHQLVsYOd2mBzkYDAdKa+dIAAAh+QQJCgAAACwAAAAAEAAQAAADNAi63P5OjCEgG4QMu7DmikRxQlFUYDEZIGBMRVsaqHwctXXf7WEYB4Ag1xjihkMZsiUkKhIAIfkECQoAAAAsAAAAABAAEAAAAzYIujIjK8pByJDMlFYvBoVjHA70GU7xSUJhmKtwHPAKzLO9HMaoKwJZ7Rf8AYPDDzKpZBqfvwQAIfkECQoAAAAsAAAAABAAEAAAAzMIumIlK8oyhpHsnFZfhYumCYUhDAQxRIdhHBGqRoKw0R8DYlJd8z0fMDgsGo/IpHI5TAAAIfkECQoAAAAsAAAAABAAEAAAAzIIunInK0rnZBTwGPNMgQwmdsNgXGJUlIWEuR5oWUIpz8pAEAMe6TwfwyYsGo/IpFKSAAAh+QQJCgAAACwAAAAAEAAQAAADMwi6IMKQORfjdOe82p4wGccc4CEuQradylesojEMBgsUc2G7sDX3lQGBMLAJibufbSlKAAAh+QQJCgAAACwAAAAAEAAQAAADMgi63P7wCRHZnFVdmgHu2nFwlWCI3WGc3TSWhUFGxTAUkGCbtgENBMJAEJsxgMLWzpEAACH5BAkKAAAALAAAAAAQABAAAAMyCLrc/jDKSatlQtScKdceCAjDII7HcQ4EMTCpyrCuUBjCYRgHVtqlAiB1YhiCnlsRkAAAOwAAAAAAAAAAAA==" />
                <router-link to="/register" class="btn btn-link">Регистрация</router-link>
            </div>
        </form>
      </div>
    </div>
</template>

<script>
import { mapState, mapActions } from 'vuex'

export default {
    data () {
        return {
            username: '',
            password: '',
            submitted: false
        }
    },
    computed: {
        ...mapState('account', ['status'])
    },
    created () {
        // reset login status
        this.logout();
    },
    methods: {
        ...mapActions('account', ['login', 'logout']),
        handleSubmit (e) {
            this.submitted = true;
            const { username, password } = this;
            if (username && password) {
                this.login({ username, password })
            }
        }
    }
};
</script>
