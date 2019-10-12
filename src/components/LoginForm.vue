<template>
    <div class="login-form">
        <div class="login-text">LOGIN</div>
        <b-form @submit.prevent="onSubmit">
            <b-alert variant="danger" :show="hasError">{{ error }} </b-alert>

                <b-form-input style="background-color: rgb(71, 74, 81);border: 1px solid rgb(70, 70, 70);color: rgb(208, 208, 208);width: 315px;margin-left: 50px;
                              margin-right: 15px;float: left;"
                              id="userInput"
                              type="text"
                              placeholder="Enter username"
                              v-model="userId"
                              autocomplete="off"
                              :disabled="loading"
                              required>
                </b-form-input>

            <b-button type="submit"
                      variant="primary"
                      class="ld-ext-right"
                      v-bind:class="{ running: loading }"
                      :disabled="isValid">
                Login <div class="ld ld-ring ld-spin"></div>
            </b-button>
            <div class="hint">Hint: use 'hamza'.</div>
            <div class="projects">More projects <a href="https://www.hamzaarshad.com">here.</a></div>
        </b-form>
    </div>
</template>

<script>
    import { mapState, mapGetters, mapActions } from 'vuex'

    export default {
        name: 'login-form',
        data() {
            return {
                userId: '',
            }
        },
        computed: {
            isValid: function() {
                const result = this.userId.length < 3;
                return result ? result : this.loading
            },
            ...mapState([
                'loading',
                'error'
            ]),
            ...mapGetters([
                'hasError'
            ])
        },
        methods: {
            ...mapActions([
                'login'
            ]),
            async onSubmit() {
                const result = await this.login(this.userId);
                if (result) {
                    this.$router.push('chat');
                }
            }
        }
    }
</script>
<style>
    .login-text{
        font-family: 'Fjalla One', sans-serif;
        color: #d0d0d0;
        font-size: 22px;
        text-align: center;
        margin-top: 30px;
    }
    .projects{
        position: absolute;
        right: 0;
        bottom: 0;
        margin: 9px;
        font-family: Montserrat, sans-serif;
        color: #999;
    }
    .hint{
        position: absolute;
        bottom: 0;
        left: 0;
        margin: 9px;
        font-family: Montserrat, sans-serif;
        color: #999;
        font-size: 14px;
    }
</style>