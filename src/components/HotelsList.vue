<template>
    <div>
        <HotelCard v-for="hotel in cutOnPage" :hotel="hotel" class="card"></HotelCard>
        <div class="btn-wrapper">
            <button class="btn" @click="page--">Назад</button>
            <span>{{page}} / {{countPage}}</span>
            <button class="btn" @click="page++">Вперед</button>
        </div>
    </div>
</template>

<script>
import HotelCard from './Hotels/HotelCard';

  export default {
    name: "HotelsList",
    props: {
      hotels: []
    },
    data() {
      return {
        pageSize: 3,
        page: 1
      }
    },
    computed: {
      cutOnPage() {
        const start = this.pageSize * (this.page - 1)
        const end = Math.min(this.pageSize * this.page, this.hotels.length)

        return this.hotels.slice(start, end)
      },
      countPage() {
        return Math.ceil(this.hotels.length/this.pageSize);
      }
    },
    watch: {
      page(newVal, oldVal) {
        if(newVal < 1) {
          this.page = oldVal;
        } else if(newVal > this.countPage) {
          this.page = oldVal;
        }
      }
    },
    components: {
      HotelCard
    }
  }
</script>

<style scoped>
.card {
    margin-top: 30px;
}
.btn-wrapper {
    display: flex;
    justify-content: space-around;

    margin-top: 40px;
}
.btn {
    border-radius: 12px;
    background-color:rgba(0, 187, 109, 0.1);
    color: #6A53F5;

    padding: 10px 30px;
}
</style>
