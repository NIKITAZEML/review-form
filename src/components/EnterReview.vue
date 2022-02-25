<template>
    <div class="review">
        <label for="review" class="label-enter-login">Отзыв</label>
        <textarea name="review" id="review" cols="50" rows="6" class="main-text-area borr-10"
                  @focus="focusReview= !focusReview"
                  :class="{ clicked :  focusReview}"
                  @blur="focusReview = !focusReview"
                  v-model="review"
                  @input="setReview"
        ></textarea>
    </div>
</template>

<script>
export default {
    name: "EnterReview",
    data(){
        return{
            focusReview: false,
        }
    },
    methods:{
        setReview(){
            this.$emit('setReview', this.review)
        }
    },
    props:{
        review: String,
    }
}
</script>

<style scoped>
.review{
    display: flex;
    flex-direction: column;
    margin-bottom: 1.389vw;
}

.label-enter-login{
    color: rgba(23, 23, 25, .3);
    font-size: 1.111vw;
}

.main-text-area{
    width: 23.194vw;
    height: 10vw;
    resize: none;
    outline: none;
    border: solid .1vw rgba(23, 23, 25, 0.2);;
    font-size: 1.389vw;
    padding: .833vw 1.042vw .833vw 1.042vw;
}

@media screen and (max-width: 768px) {
    .review{
        margin-bottom: 2.604vw;
    }

    .label-enter-login{
        font-size: 2.083vw;
    }

    .main-text-area{
        width: 43.490vw;
        height: 19vw;
        border-radius: 1.302vw;
        font-size: 2.604vw;
        padding: 1.563vw 1.953vw 1.563vw 1.953vw;
    }
}

@media screen and (max-width: 320px) {
    .review {
        margin-bottom: 10vw;
    }

    .label-enter-login {
        font-size: 5vw;
    }

    .main-text-area {
        width: 88.75vw;
        height: 50vw;
        border-radius: 3.125vw;
        font-size: 5vw;
        padding: 3.750vw 4.688vw 3.750vw 4.688vw ;
    }
}
</style>