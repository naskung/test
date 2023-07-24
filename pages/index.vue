<template>
  <MobileLayout>
    <a-layout>
      <a-layout-header>
        <div class="title">หน้าทดสอบ</div>
      </a-layout-header>
      <a-layout-content>
        <a-form-model
        ref="form"
        class="flex-form"
        :model="form"
        layout="vertical"
      >
        <a-row class="detail-title2">
          <h3>กรุณาเลือกหมายเลขด้านล่าง</h3>
            <a-form-model-item style="margin-bottom: 5">
              <input
                v-model="form.number"
                style="padding-left: 0"
                size="large"
                placeholder="0"
                class="number-input"
                readonly
              />
            </a-form-model-item>
        </a-row>
      
        <div class="switch">
          <a-switch v-model:checked="checked" @click="onToggle" />
        </div>
        <div class="topup-radio-butt">
          <template>
            <a-radio-group
            v-for="number in numberList"
            v-model="form.number"
          >
            <a-radio-button  :disabled="disabled" :value="number.numberValue">{{ number.textShow }}</a-radio-button>
          </a-radio-group>
          </template>
        </div>
        <a-row class="detail-title2">
          <h3>กรุณากรอกชื่อ</h3>
          <a-input  v-model="form.textFirst" placeholder="First Name" />
        </a-row>
        <a-row class="detail-title2">
            <h3>กรุณากรอกนามสกุล</h3>
            <a-input  v-model ="form.textLast" placeholder="Last Name" />
        </a-row>
        <div>
          <h3>กรุณากรอกที่อยู่</h3>
          <a-textarea
            v-model="form.adress"
            placeholder="Adress"
            :auto-size="{ minRows: 2, maxRows: 5 }"
          />
        </div>
      
      </a-form-model>
  
      </a-layout-content>
  
      <a-layout-footer>
        <a-row class="button-row">
          <a-button
            id="submit-button"
            size="large"
            @click="onClickSubmit"
          >
            ถัดไป
          </a-button>
        </a-row>
      </a-layout-footer>
    </a-layout>
  </MobileLayout>
</template>

<script>
  export default {
    data() {
      return {
        form: {
          number: null,
          textFirst: null,
          textLast: null,
          adress:null,
        },
        checked : false,
        disabled : true,

        numberList: [
          { numberValue: '1', textShow: '1' },
          { numberValue: '2', textShow: '2' },
          { numberValue: '3', textShow: '3' },
          { numberValue: '4', textShow: '4' },
        ],
      }
    },
  methods: {
    onToggle(){
      this.disabled =! this.disabled
    },
    onClickSubmit(){
      this.$router.push({
        path: 'confirm',
        params: {},
        query: {
          number: this.form.number,
          textFirst: this.form.textFirst,
          textLast: this.form.textLast,
          adress: this.form.adress
        },
      })
    },
  },
       
}
</script>



<style scoped>
.title {
  color: white;
  text-align: center;
}
.ant-layout-header {
  background: rgb(44, 16, 16);
}
.ant-layout-content {
  padding: 10px;
}
.switch {
  margin-bottom:20px;
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
.button-row {
  align-self: start;
  padding: 20px;
  margin-top: auto;
}
.ant-layout-footer{
  text-align: center;
}

</style>
