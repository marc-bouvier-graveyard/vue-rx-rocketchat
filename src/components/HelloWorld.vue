<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <ul v-for="message in messages">
      <li>{{message}}</li>
    </ul>
  </div>
</template>

<script>
  import {RealTimeAPI} from "rocket.chat.realtime.api.rxjs"

  export default {
    name: 'HelloWorld',
    created() {
      const realTimeAPI = new RealTimeAPI ("wss://open.rocket.chat/websocket")
      // Provide, URL to the Rocket.Chat's Realtime API.
      realTimeAPI.onError (err => console.log ("Realtime API Error", err))
      realTimeAPI.onCompletion (() => console.log ("Realtime API Complete"))
      realTimeAPI.onMessage (realTimeMessage => this.messages.push (JSON.stringify (realTimeMessage)))
      const connection = realTimeAPI.connectToServer ()
      let auth
      connection.subscribe (() => {
        realTimeAPI.keepAlive () // Ping Server
        // Responds "pong" to the "ping" message sent by the Realtime API. To keep the connection alive.

        // Creating Observable
        auth = realTimeAPI.login ('marc.test', 'trello@w3bx.com')
        // Now subscribing the observable
        auth.subscribe (
          (data) => {
            console.log ('completed')
            realTimeAPI.sendMessage ({
              msg: 'sub',
              id: 'idfdsfsfsfs',
              name: 'stream-room-messages',
              params: ['GENERAL', false]
            })
          },
          (err) => console.log (err),
          () => {
          })
      })
    },
    data() {
      return {
        msg: 'Welcome to Your Vue.js App',
        messages: []
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1, h2 {
    font-weight: normal;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    display: inline-block;
    margin: 0 10px;
  }

  a {
    color: #42b983;
  }
</style>
