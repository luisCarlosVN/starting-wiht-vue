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
        <br/>
        <div v-if="type === 'A'">
            A
        </div>
        <div v-else-if="type === 'B'">
            B
        </div>
        <div v-else-if="type === 'C'">
            C
        </div>
        <div v-else>
            Si no es A, B o C
        </div>
        <br/>
        <div>
            <button type="button" class="btn btn-primary" @click="test">Llamar al metodo</button>
            <div class="divider"/>
            <button type="button" class="btn btn-success" @click="testWithParameters('Pepe')"> Llamando al metodo con parametros</button>
        </div>
        <ul id="example-1">
            <li v-for="user in users" :key="user.id">
                {{ user.firstName}}
            </li>
        </ul>
    </div>
</template>

<script>
import { ref } from "vue";

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
    },
    methods: {
        increment()
        {
            this.count+= 1;
        },
        decrement()
        {
            this.count-= 1;
        },
        test: function()
        {
            alert('prueba de la funcion con mensaje' + this.message);
        },
        testWithParameters: function(name)
        {
                alert('Hola' + name);
        }
    },
    setup()
    {
        //alert('este mensaje es ' + props.message')
        // make users variable reactive with the ref() function
        const users = ref([
            { firstName: 'Frank', lastName:'Murphy', age: 24},
            { firstName: 'Vic', lastName:'SAnj', age: 30},
            { firstName: 'Gina', lastName:'Tonic', age: 40},
            { firstName: 'Jessi', lastName:'James', age: 50},
            { firstName: 'Jay', lastName:'Tack', age: 60}
        ]);

        return {
            users
        };
    }

}
</script>