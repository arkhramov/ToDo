<template>
    <div>
      <div style="display: inline-block;">
        <h1 style="text-align: center">Привет, {{account.user.firstName}}!</h1>
        <router-link to="/login">Выход</router-link>
      </div>
      <h2 style="text-align: center">Список задач</h2>
      <todo-list />
    </div>
</template>

<script>
import { mapState, mapActions } from 'vuex'
import TodoList from "../components/TodoList";

export default {
    components: {
      TodoList
    },
    computed: {
        ...mapState({
            account: state => state.account,
            users: state => state.users.all
        })
    },
    created () {
        this.getAllUsers();
    },
    methods: {
        ...mapActions('users', {
            getAllUsers: 'getAll',
            deleteUser: 'delete'
        })
    }
};
</script>
