<template>
    <div class="message-list">
        <span class="channel-header">
            {{activeRoom.name.toUpperCase()}}
        </span>
        <hr>
        <div id="chat-messages" class="message-group" v-chat-scroll="{smooth: true}">
            <div class="message" style="border:none; border-top: 1px solid rgb(81,81,81)" v-for="(message, index) in messages" :key="index">
                <div class="clearfix">
                    <span style="font-family: 'Lato', sans-serif;color: #d0d0d0; cursor: pointer;" class="message-title">{{ message.name }} </span>
                    <small class="text-muted" style="font-size: 10px;"> at {{ message.date }}</small>
                    <small class="text-muted float-right">@{{ message.username }}</small>
                </div>
                <p style="font-family: 'Lato', sans-serif;font-size:14px" class="message-text">
                    {{ message.text }}
                </p>

            </div>
        </div>
        <div class="user-typing">
            <small class="text-muted" v-if="userTyping">@{{ userTyping }} is typing....</small>
        </div>
    </div>
</template>

<script>
    import { mapState } from 'vuex'

    export default {
        name: 'message-list',
        computed: {
            ...mapState([
                'messages',
                'activeRoom',
                'userTyping'
            ])
        }
    }
</script>

<style>
    .message-list {
        margin-bottom: 15px;
        padding-right: 15px;
    }
    .message-group {
        height: 70vh !important;
        overflow-y: scroll;
    }
    .message {
        border: 1px solid lightblue;
        border-radius: 4px;
        padding: 10px;
        margin-bottom: 15px;
    }
    .message-title {
        font-size: 1rem;
        display:inline;
    }
    .message-text {
        color: gray;
        margin-bottom: 0;
    }
    .user-typing {
        height: 1rem;
    }
    ::-webkit-scrollbar {
        width: 10px;
        background-color: rgb(60, 64, 66);
    }

    /* Track */
    ::-webkit-scrollbar-track {
        background-color: rgb(60, 64, 66);
    }

    /* Handle */
    ::-webkit-scrollbar-thumb {
        background: #888;
    }

</style>