<template>
    <div class="window-auth borr-10">
        <div class="auth__entrance-heading">
            Форма отзывов
        </div>
        <form @submit.prevent="sendData">
            <enter-login :login="login" @setLogin="setLogin"></enter-login>
            <enter-phone :phone="phone" @setphone="setphone"></enter-phone>
            <enter-review :review="review" @setReview="setReview"></enter-review>
            <button class="entry-btn" type="submit" >
                Отправить
            </button>
        </form>
    </div>
</template>

<script>
import EnterLogin from './EnterLogin';
import EnterPhone from './EnterPhone';
import EnterReview from "./EnterReview";
import axios from "axios";

export default {
    name: "AuthWindow",
    data(){
      return{
          login: '',
          phone: '',
          review: '',
          errors: [],
      }
    },
    methods:{
        setLogin(newLogin){
            this.login = newLogin;
        },
        setphone(newphone){
            this.phone = newphone;
        },
        setReview(newReview){
            this.review = newReview;
        },
        sendData(){
            axios.post(`http://127.0.0.1:8000/api/review/`, {
                name: this.login, phone: this.phone, review: this.review
            })
            .then( response => {
                console.log(response)
            })
        }
    },
    components:{
        EnterReview,
        EnterLogin,
        EnterPhone,
    }
}
</script>

<style scoped>
    .window-auth{
        width: 35.417vw;
        height: 39vw;
        border: .1vw rgba(39, 39, 39, .1) solid;
        background-color: #fff;
        display: flex;
        flex-direction: column;
        align-items: center;
        margin: 0 auto;
        position: absolute;
        top: 50%;
        left: 50%;
        margin-right: -50%;
        transform: translate(-50%, -50%)
    }

    .auth__entrance-heading{
        margin-bottom: 1.389vw;
        margin-top:1.389vw; ;
        font-weight: 500;
        font-size: 1.25vw;
    }
    
    .entry-btn{
        color: #fff;
        border-radius: .347vw;
        width: 12.222vw;
        height: 3.611vw;
        background-color: #1390E5;
        border: 0;
    }

    @media screen and (max-width: 768px) {
        .window-auth{
            width: 66.406vw;
            height: 67.708vw;
        }

        .auth__entrance-heading{
            margin-bottom: 2.604vw;
            font-size: 2.344vw;
        }

        .entry-btn{
            font-size: 2.604vw;
            border-radius: .651vw;
            width: 22.917vw;
            height: 6.771vw;
        }
    }

    @media screen and (max-width: 320px) {
        .window-auth{
            margin-top: 20vw;
            width: 95vw;
            height: 200vw;
            position: static;
            top: 0;
            left: 0;
            margin-right: 2.5%;
            transform: none;
        }


        .auth__entrance-heading{
            margin-top: 15vw;
            margin-bottom: 6.25vw;
            font-size: 5.625vw;
        }

        .entry-btn{
            border-radius: 1.563vw;
            font-size: 6.25vw;
            width: 55vw;
            height: 16.25vw;
        }
    }
</style>

