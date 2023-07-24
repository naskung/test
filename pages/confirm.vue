<template>
  <MobileLayout>
    <a-layout>
      <a-layout-header>
        <div class="title">โชว์ข้อมูล</div>
      </a-layout-header>
      <a-layout-content>
        <a-row class="detail-title2">
          <h3>ชื่อ</h3>
          <div>{{ textFirst }}{{ textLast }}
          <button @click="onDeleteText">ลบ</button>
        </div>
          <h3>ที่อยู่</h3>
          <div>{{  adress }}
            <button @click="onDeleteAdress">ลบ</button>
          </div>
          <h3>หมายเลข</h3>
          <div>{{ number }} <button @click="onDelete">ลบ</button></div>
        </a-row>
      </a-layout-content>
    </a-layout>
  </MobileLayout>
</template>

<script>
  export default {
    data() {
      return {
          number: this.$route.query.number,
          textFirst: this.$route.query.textFirst,
          textLast: this.$route.query.textLast,
          adress: this.$route.query.adress,
      }
    },
    methods: {
      onDeleteText () {
        this.textFirst = null,
        this.textLast = null
      },
      onDeleteAdress () {
        this.adress = null
      },
      onDelete () {
        this.number = null
      }
    }
    
}
</script>

<style scoped>
.title {
  color: white;
  text-align: center;
}
.ant-layout-content {
  padding: 10px;
}
.number-input{
  font-size: 30px;
  font-weight: 700;
  padding-top: 10px;
  padding-left: 20px;
  line-height: 1.7;
  border-radius: 0;
  border-width: 0 0 1px 0 !important;
  border-color: #b4becb;
  background-color: transparent !important;
  box-shadow: none !important;
  height: 60px;
  width: 100%;
}

</style>