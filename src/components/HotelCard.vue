<template>
    <div class="card">
        <div class="card-content">
            <h3>{{hotel.name}}</h3>
            <div class="info-content">
                <span class="info-content-element">
                    <star-rating :max="5" :current="hotel.stars"></star-rating>
                </span>
                <span class="info-content-element">{{hotel.type}}</span>
                <span class="info-content-element">{{hotel.reviews_amount + ' ' + reviews}}</span>
                <span>&#9971; {{hotel.country}}</span>
            </div>
            <p>{{hotel.description}}</p>

        </div>
        <div class="card-price">
            <p>{{hotel.min_price}} руб</p>
            <button class="blocked">Забронировать</button>
        </div>
    </div>
</template>

<script>
    import {declOfNum} from '../utils';
    import starRating from './starRating';
  export default {
    name: "HotelCard",
    props: {
      hotel: {}
    },
    computed: {
      reviews() {
        return declOfNum(this.hotel.reviews_amount, ['отзыв', 'отзыва', 'отзывов'])
      }
    },
    components: {
      starRating
    }
  }
</script>

<style scoped>
.card {
    border: 1px solid #EAEAEA;
    border-radius: 15px;

    padding: 25px;

    display: flex;
    justify-content: space-between;
}

.card-content {
    width: 70%;
}

.info-content {
    display: flex;
    align-items: center;

}

.info-content-element {
    margin-right: 15px;
}

.card-price {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    justify-content: space-around;
    width: 30%;
}

.blocked {
    border-radius: 12px;
    background-color:rgba(0, 187, 109, 0.1);
    color: #6A53F5;

    padding: 10px 30px;
}
</style>
