<script>
    export default  {
        name: "Pangram",
        data(){
            return {
                input: '',
                status:'',
                used_alphas: ''
            }
        },
        watch:{
            input: {
                handler: function () {
                    this.checkPangram();
                }
            }
        },
        methods: {
            checkPangram() {
//                c = String.fromCharCode(i);
                let vm = this;
                let alphabets = [];
                let i = 'A'.charCodeAt(0);
                let j = 'Z'.charCodeAt(0);

                for (; i <= j; ++i) {
                    alphabets.push(String.fromCharCode(i));
                }
                let s = this.input.replace(' ','').split('')
                let state = 0;


            let used_alphas = s.filter(function(item, i, ar){ return ar.indexOf(item) === i; }).join('');
            this.used_alphas = used_alphas;

                if (used_alphas.length >= 26) {
                    this.status = 'We have ourselves a pangram'
                } else {
                    this.status = 'Data not enough to qualify a pangram';
                }

            }



        }
    }
</script>
<template>
    <div>
        <form >
            <input type="text" v-model="input">

            <h5>{{status}}</h5>
            <p v-show="used_alphas != '' ">Used characters are: {{used_alphas}}</p>
        </form>
    </div>
</template>

<style>

</style>