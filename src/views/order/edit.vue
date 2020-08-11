<template>
  <div class="order-edit-container">
    <el-form ref="form" :model="form" label-width="80px">
      <el-form-item label="订单编号">
        <el-input v-model="form.orderNo" />
      </el-form-item>
      <el-form-item label="厂家">
        <el-input v-model="form.manufacturer" />
      </el-form-item>
    </el-form>
  </div>
</template>
<script>
export default {
  name: 'OrderEdit',
  data() {
    return {
      form: {
        orderNo: '',
        manufacturer: ''
      }
    }
  }
}
</script>
