<template>
    <div class="cont d-flex flex-wrap">
        <div class="form-group mb-4" id="card-number-field">
                <label for="name">cardholder name</label>
                <input type="text" class="form-control" v-model="name" @keyup="$emit('name',name)" id="name" placeholder="e.g. Francesco Ciano">
        </div>
        <div class="form-group mb-4" id="card-number-field">
                <label for="cardNumber">Card Number</label>
                <input type="txt" class="form-control" v-model="cardNumber"  @keyup="$emit('cardNumber',cardNumber),cardNumberFormat()" id="cardNumber" placeholder="e.g. 1234 5678 9123 0000">
        </div>
        <div class="form-group w-50" id="expiration-date-field">
            <label class="w-100" for="expiration-date">EXP. Date (MM/YY)</label>
            <input type="number" maxlength="2" class="form-control d-inline-block me-1" v-model="expirationDateMonth" @keyup="$emit('expirationDateMonth',expirationDateMonth)" id="expirationDateMonth" placeholder="MM">
            <input type="number" maxlength="2" class="form-control d-inline" v-model="expirationDateYear" @keyup="$emit('expirationDateYear',expirationDateYear)" id="expirationDateYear" placeholder="YY">
        </div>
        <div class="form-group w-50 mb-4" id="cvv-field">
            <label for="cvv">CVV</label>
            <input type="number" maxlength="3" class="form-control" v-model="cvv" @keyup="$emit('cvv',cvv)" id="cvv" placeholder="e.g. 123">
        </div>
        <button type="button" class="btn btn-dark py-2">confirm</button>
    </div>
</template>

<script>
export default {
    name:'DataEntery',
    data(){
        return{
            name:null,
            cardNumber:null,
            expirationDateMonth:null,
            expirationDateYear:null,
            cvv:null,
        }
    },
    methods:{
        cardNumberFormat(){
            if (this.cardNumber.length==4||this.cardNumber.length==9||this.cardNumber.length==14){
                this.cardNumber+=" ";
            }
        }
    }
}
</script>

<style lang="scss" scoped>
@import '~bootstrap/scss/bootstrap';
@include media-breakpoint-down(md){
    .cont{
        width: 100%;
        margin-top: 23vh;
        padding: 2vh 8vw;
        font-size: 4vw;
    }
}
@include media-breakpoint-up(md) {
    .cont{
    top: 7vh;
    right: 10vw;
    font-size: .9rem;
    width: 28vw;
    padding: 15vh 0;
    }
}

@include media-breakpoint-up(xl) {
    .cont{
    top: 12vh;
    right: 15vw;
    font-size: 1.15rem;
}
}
.cont{
    position: absolute;
        &>*{
            width: 100%;
        }
        & *{
            box-shadow: none !important;
        }
        // width: 28vw;
        text-transform: uppercase;
        #expirationDateMonth,#expirationDateYear{
            width: 47%;
        }
        label{
            margin-bottom: 7px;
        }
        input::-webkit-outer-spin-button,
        input::-webkit-inner-spin-button {
        -webkit-appearance: none;
        margin: 0;
        }   
    }
</style>