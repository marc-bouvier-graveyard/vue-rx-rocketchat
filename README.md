# vue-rx-rocketchat

> POC using vuejs, rxjs and rocketchat

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev
```

### Testing with demo site of rocket.chat

In modern browser this is working. Is fails in Internet explorer 11.
- Run the application : `npm run dev`.
- Go to [https://open.rocket.chat](https://open.rocket.chat) and create an account.
- Go to #general channel and type any message
- messages of #general channel should appear in vuejs application

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

In internet explorer the following error occurs when trying to subscribe to channel 'GENERAL' : 
```   
TypeError: L’objet ne gère pas la propriété ou la méthode « find »
   {
      [functions]: ,
      __proto__: { },
      description: "L’objet ne gère pas la propriété ou la méthode « find »",
      message: "L’objet ne gère pas la propriété ou la méthode « find »",
      name: "TypeError",
      number: -2146827850,
      stack: "TypeError: L’objet ne gère pas la propriété ou la méthode « find »
   at Anonymous function (eval code:154:99)
   at FindValueSubscriber.prototype._next (eval code:85:13)
   at Subscriber.prototype.next (eval code:89:13)
   at BufferSubscriber.prototype.notifyNext (eval code:74:9)
   at InnerSubscriber.prototype._next (eval code:23:9)
   at Subscriber.prototype.next (eval code:89:13)
   at FilterSubscriber.prototype._next (eval code:89:13)
   at Subscriber.prototype.next (eval code:89:13)
   at Subscriber.prototype._next (eval code:125:9)
   at Subscriber.prototype.next (eval code:89:13)"
   }
``` 
