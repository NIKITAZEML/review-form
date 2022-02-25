<template>
    <div class="enter-phone">
        <label class="label-enter-phone" for="input-phone">Телефон</label>
        <input type="number" class="input-phone" id="input-phone"
               @focus="focusphone = !focusphone"
               :class="{ clicked :  focusphone}"
               @blur="focusphone = !focusphone"
               v-model="phone"
               @input="setphone">
    </div>
</template>

<script>
export default {
    name: "Enterphone",
    data () {
        return{
            focusphone: false,
        }
    },
    props:{
        phone: String,
    },
    methods:{
        setphone(){
            this.$emit('setphone', this.phone)
        }
    },
}
</script>

<style scoped>
.enter-phone{
    position: relative;
    display: flex;
    flex-direction: column;
    margin-bottom: 2.778vw;
}

.label-enter-phone{
    color: rgba(23, 23, 25, .3);
    font-size: 1.111vw;
}

.input-phone{
    width: 23.194vw;
    height: 3.333vw;
    font-size: 1.389vw;
    padding: .833vw 1.042vw .833vw 1.042vw;
}



@media screen and (max-width: 768px) {
    .enter-phone{
        margin-bottom: 2.604vw;
    }

    .label-enter-phone{
        font-size: 2.083vw;
    }

    .input-phone{
        width: 43.490vw;
        height: 6.250vw;
        font-size: 2.604vw;
        padding: 1.563vw 1.953vw 1.563vw 1.953vw;
    }

}

@media screen and (max-width: 320px) {
    .enter-phone {
        margin-bottom: 10vw;
    }

    .label-enter-phone {
        font-size: 5vw;
    }

    .input-phone {
        width: 88.75vw;
        height: 15vw;
        font-size: 5vw;
        padding: 3.750vw 4.688vw 3.750vw 4.688vw ;
    }

}
</style>