<template>
    <div class="row">
        <div class="col-lg-12 text-center">
            <h1>{{ title }}</h1>
        </div>

        <div class="col-lg-12">
            <h2>{{ instanceMethod }}</h2>
            <strong>{{ myFullName() }}</strong>
        </div>

        <div class="col-lg-12">
            <h2>{{ instanceMethodObject }}</h2>
            <pre>
                {{ myFullNameObject() }}
            </pre>
        </div>

        <div class="col-lg-12">
            <h2>{{ instanceMethodComputed }}</h2>
            <strong>{{ aLuas }}</strong>
        </div>

        <div class="col-lg-12">
            <h2>{{ template }}</h2>
            <div v-html="templateeHtml"></div>
            <img src = "@/assets/london.jpg" width="300px" height= "150px"/>
        </div>

        <div class="col-lg-12">
            <h2>{{ newComponentTitle }}</h2>
            <newComponent/>
        </div>

        <div class="col-lg-12">
            <h2>{{ computedProperties }}</h2>
            <input type="text" v-model="firstNameProp" />
            <input type="text" v-model="lastNameProp" />
            <br>
            My Full Name is {{ firstNameProp }} {{ lastNameProp}}
            Using Computed Properties {{ getFullNameProp }}
        </div>

        <div class="col-lg-12">
            <h2>{{ getComputedProperties }}</h2>
            <input type="text" v-model="fullNameGetProp" />
            <br>
            <p>{{ firstNameGetProp }}</p>
            <p>{{ lastNameGetProp }}</p>
        </div>

        <div class="col-lg-12">
            <h2>{{ computedProperties }}</h2>
            <input type="text" v-model="kilometers" />
            <input type="text" v-model="meters" />
            <br>
        </div>

        <div class="col-lg-12">
            <h2>{{ binding }}</h2>
            <a v-bind:href = "hrefLink" target="_blank">Clik Me</a>
            <div v-bind:class = "{active:isActive}">Class Binding</div>
            <div class="info" v-bind:class = "{ active: isActive, displayError: hasError }">Multiple Binding Class</div>
            <div v-bind:class = "[infoClass, errorClass]">Array Binding Class</div>
            <div v-bind:class = "[isActive ? infoClass: '', hasError ? errorClass: '']">Condition Binding Class</div>
            <component-class v-bind:class = "{active:isActive}"></component-class>
            <div v-bind:style = "{ color: activeColor, fontSize: + 'px' }">Style Inline Binding</div>
            <div v-bind:style = "styleObject">Style Object Binding</div>
        </div>

        <div class="col-lg-12">
            <h2>{{ bindingForm }}</h2>
            <input type="text" v-model="name" placeholder="Enter Name"/>
            <br>
            {{ name }}
            <br>
            <textarea v-model="address" placeholder="Enter Address"/>
            <br>
            {{ address }}
            <br>
            <input type="checkbox" v-model="checked"/>
            <br>
            {{ checked }}
            <br>
            <input type="radio" value="Black" v-model="picked">Black
            <input type="radio" value="White" v-model="picked">White
            <br>
            Radio element clicked is {{ picked }}
            <br>
            <select v-model = "languagesForm">
                <option disabled value = "">Please select one</option>
                <option>Java</option>
                <option>Javascript</option>
                <option>Php</option>
                <option>C</option>
                <option>C++</option>
            </select>
            Languages Selected is : {{ languagesForm }}
            <br>
            <input type="number" v-model.number = "age" placeholder="Input Number"/>
            <br>
            <input  v-model.lazy = "msg"/>
            <br>
            Display Message {{ msg }}
            <br>
            <input  v-model.trim = "message" />
            <br>
            Display message {{ message }}
        </div>

        <div class="col-lg-12">
            <h2>{{ events }}</h2>
            <button v-on:click = "displayNumbers">Clik Me</button>
            <button @click = "displayNumbers">Clik Me (Shorten)</button>
            Add Number 100 + 200 = {{ total }}
            <br>
            <div v-bind:style = "styleObjectEvent" v-on:mouseover = "changeColor" v-on:mouseout = "originalColor"></div>
            <button v-on:click.once = "butttonclickedonce">Click Once</button>
            <br>
            Output {{ clicknum }}
            <br>
            <button v-on:click = "butttonclicked">Click Not Once</button>
            <br>
            Output {{ clicknum1 }}
            <br>
            <a href = "http://faridho.com" v-on:click.prevent = "clickprevent" target="_blank">Clik Prevent</a>
        </div>

        <div class="col-lg-12">
            <h2>{{ eventCustom }}</h2>
            <p style = "font-size:25px;">Language displayed : <b>{{ languageclicked }}</b></p>
            <button-counter
            v-for = "(item, index) in languages"
            v-bind:item = "item"
            v-bind:index = "index"
            v-bind:key = "item.id"
            v-on:showlanguage = "languagedisp"></button-counter>
        </div>

        <div class="col-lg-12">
            <h2>{{ rendering }}</h2>
            <button v-on:click = "showData">Click Me</button>
            <p v-if = "show"> Im first </p>
            <p v-else> im second </p>
            <br>
            <div v-show = "show">
                <b>v-show</b>
                <img src = "@/assets/london.jpg" width="300px" height= "150px"/>
            </div>
            <br>
            <p>Looping</p>
            <ul>
                <li 
                    v-for = "(item, index) in fruits"
                    v-bind:item = "item"
                    v-bind:index = "index"
                    v-bind:key = "item.id"
                >{{ item }}</li>
            </ul>
            <p>Looping Search</p>
            <input type="text" v-on:keyup.enter = "showInputValue">
            <ul>
                <li 
                    v-for = "(item, index) in fruits_2"
                    v-bind:item = "item"
                    v-bind:index = "index"
                    v-bind:key = "item.id"
                >{{ item }}</li>
            </ul>
        </div>

        <div class="col-lg-12">
            <h2>{{ filterDirective }}</h2>
            <input v-model = 'filterName' placeholder = "Enter Name">
            Letter count is {{ filterName | countletters }}
        </div>
    </div>
</template>

<script>
import newComponent from '@/components/NewComponent'
export default {
    name: 'GetStarted',
    
    data () {
        return {
            title: 'Hello Vue',
            instanceMethod: 'Instance Method',
            instanceMethodObject: 'Instance Method Object',
            instanceMethodComputed: 'Instance Method Computed',

            template: 'Template',
            templateeHtml: "<div class='alert alert-success'>Try Template</div>",

            newComponentTitle: 'New Component',

            computedProperties: 'Computed Properties',
            firstNameProp: '',
            lastNameProp: '',

            getComputedProperties: 'Get Computed Properties',
            firstNameGetProp: 'Faridho',
            lastNameGetProp: 'Lionardhio',

            watchProperty: 'Watch Property',
            kilometers: 0,
            meters: 0,

            binding: 'Binding Class & Style',
            hrefLink: 'http://faridho.com',
            isActive: false,
            hasError: false,
            infoClass: 'info',
            errorClass: 'displayError',
            activeColor: 'green',
            fontSize: '30',
            styleObject: {
                color: 'yellow',
                fontSize: '40px'
            },

            bindingForm: 'Binding Form',
            
            firstName: 'Faridho',
            lastName: 'Lionardhio',

            obj : {
                fName: "Fraidho",
                lName: "Lionardhio"
            },
            
            luas: 6,
            tinggi: 2,

            name: '',
            address: '',
            checked: false,
            picked: 'White',
            languagesForm: "Java",

            age: 0,
            msg: '',
            message: '',

            events: 'Events',
            num1: 100,
            num2: 200,
            total : '',
            styleObjectEvent: {
                width: "100px",
                height: "100px",
                backgroundColor: "red"
            },
            clicknum: 0,
            clicknum1: 0,

            eventKeyModifiers: 'Key Modifiers',
            enterName: '',

            eventCustom: 'Event Custom',
            languageclicked: '',
            languages: ["Java", "PHP", "C++", "C", "Javascript", "C#", "Python", "HTML"],

            rendering: 'Rendering',
            show: true,
            fruits: ['Banana', 'Apple'],
            fruits_2: [],

            filterDirective: "Filter Directive",
            filterName: '',


        }
    },
    methods: {
        myFullName : function () {
            return "My Name Is " + this.firstName + ' ' + this.lastName;
        },

        myFullNameObject: function () {
            return this.obj
        },

        displayNumbers: function(event) {
            console.log(event);
            return this.total = this.num1 + this.num2; 
        },

        changeColor: function () {
            this.styleObjectEvent.backgroundColor = "green";
        },

        originalColor: function () {
            this.styleObjectEvent.backgroundColor = "red";
        },

        butttonclickedonce: function () {
            this.clicknum++;
        },

        butttonclicked: function () {
            this.clicknum1++;
        },

        clickprevent: function (){
            alert("will visit faridho.com ?");
        },

        showInputValue: function (event) {
            this.enterName = event.target.value;
        },

        languagedisp: function (a) {
            this.languageclicked = a;
        },

        showData: function() {
            this.show = !this.show;
        },

        showInputValue: function(event) {
            this.fruits_2.push(event.target.value);
        },

    },

    computed: {
        aLuas: function () {
            return "Luas adalah " + (this.luas * this.tinggi)/ 2;
        },

        getFullNameProp: function() {
            return this.firstNameProp + ' ' + this.lastNameProp;
        },

        fullNameGetProp: {
            get: function() {
                return this.firstNameGetProp + ' ' + this.lastNameGetProp;
            },

            set: function(name){
                var fName = name.split(" ");
                this.firstNameGetProp = fName[0];
                this.lastNameGetProp = fName[1];
            }
        },

    },

    watch: {
        kilometers: function(val){
            this.kilometers = val;
            this.meters = val * 1000;
        },

        meters: function(val) {
            this.kilometers = val/1000;
            this.meters = val;
        }
    },

    components: {
        'component-class': {
            template: "<div class='info'>Class Binding From Component</div>"
        },
        newComponent,

        'button-counter': {
            template: "<button v-on:click = 'displayLanguage(item)'>{{ item }}</button>",
            data: function () {
                return {
                    counter:  0
                }
            },
            props: ['item'],
            methods: {
                displayLanguage: function (lng) {
                    this.$emit('showlanguage', lng);
                }
            }
        }
    },

    filters: {
        countletters: function (value) {
            return value.length;
        }
    }
}
</script>
<style>
    .info {
        color: #00529B;
        background-color: #BDE5F8;
    }
    .active {
        background: yellow;
    }

    .displayError{
        color: #D8000C;
        background-color: #FFBABA;
    }
</style>

