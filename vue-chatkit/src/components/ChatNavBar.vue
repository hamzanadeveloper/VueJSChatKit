<template>
    <b-navbar id="chat-navbar" toggleable="md" type="dark" variant="info">
        <b-navbar-brand class="vue-title" href="#">VUECHAT</b-navbar-brand>
        <b-navbar-nav class="ml-auto">
            <b-nav-text class="nav-text">{{ user.name }} | </b-nav-text>
            <b-nav-item class="nav-text" href="#" @click="onLogout" active>Logout</b-nav-item>
        </b-navbar-nav>
    </b-navbar>
</template>

<script>
    import { mapState, mapActions, mapMutations } from 'vuex'
    // Arbitrarily decided to put reconnections into the ChatNavbar
    export default {
        name: 'ChatNavBar',
        computed: {
            ...mapState([
                'user',
                'reconnect'
            ])
        },
        methods: {
            ...mapActions([
                'logout',
                'login'
            ]),
            ...mapMutations([
                'setReconnect'
            ]),
            onLogout() {
                this.$router.push({ path: '/' });
                this.logout();
            },
            unload() {
                if(this.user.username) { // User hasn't logged out
                    this.setReconnect(true);
                }
            }
        },
        mounted() {
            window.addEventListener('beforeunload', this.unload);
            if(this.reconnect) {
                this.login(this.user.username);
            }
        }
    }
</script>

<style>
    @import url('https://fonts.googleapis.com/css?family=Fjalla+One|Montserrat&display=swap');

    #chat-navbar {
        margin-bottom: 15px;
        background-color: rgb(46,49,53) !important;
        -webkit-box-shadow:0px 1px 1px #060106;
        -moz-box-shadow:0px 1px 1px #060106;
        box-shadow:0px 1px 1px #060106;
    }

    .vue-title{
        font-family: 'Fjalla One', sans-serif;
    }

    .nav-text{
        font-family: 'Montserrat', sans-serif;
    }
</style>