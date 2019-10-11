<template>
    <div class="chat-dashboard">
        <ChatNavBar style="margin-bottom: 0" />
        <b-container fluid class="ld-over" v-bind:class="{ running: loading }">
        <div class="ld ld-ring ld-spin"></div>
        <b-row>
            <b-col class="side-container"  cols="2">
                <RoomList />
            </b-col>

            <b-col class="main-container" cols="8">
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
    .main-container{
        background: rgb(60, 64, 66);
        padding-top: 15px;
        margin-bottom: -23px;
        padding-bottom: 8px;
        border-left: 1px solid rgb(70, 70, 70);
        border-right: 1px solid rgb(70, 70, 70);
    }
</style>