<template>
    <div class="hello">
        <div>
            <h1> {{ msg }}</h1>
            <p> Hello World from Your Starter Component</p>
            <br/>
            <p> 
                {{ count }} <br/>
                <button @click="increment">+</button>
                <button @click="decrement">-</button>
            </p>
        </div>
        <br/>
        <div>
            <p> Mensaje original: "{{ msg }}"</p>
            <p> Mensaje invertido computado: "{{ reverseMsg }}"</p>
            
        </div>
        <br/>
        <div v-if="Math.random() > 0.5">
            Ahora me ves
        </div>
        <div v-else>
            Ahora no
        </div>
    </div>
</template>

<script>
//import { ref } from "vue";

export default
{
    name: 'StartingWithVue',
    props: {
        msg: {required: true, type: String},
        type: {default: 'A', type: String}
    },
    data: () => ({
        count: 0
    }),
    computed: {
        reverseMsg: function () {
            return this.msg.split('').reverse().join('')
        }
    }

}
</script>