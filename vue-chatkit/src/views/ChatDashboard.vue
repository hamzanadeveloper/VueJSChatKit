<template>
    <div class="chat-dashboard">
        <ChatNavBar style="margin-bottom: 0" />
        <b-container fluid class="ld-over" v-bind:class="{ running: loading }">
        <div class="ld ld-ring ld-spin"></div>
        <b-row>
            <b-col class="side-container"  cols="2">
                <RoomList />
            </b-col>

            <b-col cols="8">
                <b-row>
                    <b-col id="chat-content">
                        <MessageList />
                    </b-col>
                </b-row>
                <b-row>
                    <b-col>
                        <MessageForm />
                    </b-col>
                </b-row>
            </b-col>

            <b-col class="side-container" cols="2">
                <UserList />
            </b-col>
        </b-row>
        </b-container>
    </div>
</template>

<script>
    import ChatNavBar from '../components/ChatNavBar.vue'
    import RoomList from '../components/RoomList.vue'
    import MessageList from '../components/MessageList.vue'
    import MessageForm from '../components/MessageForm.vue'
    import UserList from '../components/UserList.vue'
    import { mapState } from 'vuex';

    export default {
        name: 'Chat',
        components: {
            ChatNavBar,
            RoomList,
            UserList,
            MessageList,
            MessageForm
        },
        computed: {
            ...mapState([
                'loading'
            ])
        }
    }
</script>

<style>
    .side-container{
        background: rgb(53,56,58);
        padding-top: 15px;
        margin-bottom: -23px;
    }
</style>