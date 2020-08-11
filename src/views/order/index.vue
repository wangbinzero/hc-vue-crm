<template>
  <div class="order-container">
<!--    1.listLoading 加载动画-->
<!--    2.list 数据集合-->
    <el-table v-loading="listLoading" :data="list">
      <el-table-column align="center" label="ID" width="80%">
        <template slot-scope="scope">
          <span>{{ scope.row.id}}</span>
        </template>
      </el-table-column>
      <el-table-column align="center" label="订单编号">
        <span>HC202008111202</span>
      </el-table-column>
      <el-table-column align="center" label="产品名称">
        <span>工程保险</span>
      </el-table-column>
      <el-table-column align="center" label="数量">
        <span>20</span>
      </el-table-column>
      <el-table-column align="center" label="规格">
        <span>上下</span>
      </el-table-column>
      <el-table-column align="center" label="加急订单">
        <svg-icon :key="n" icon-class="star" class="meta-item__icon" />
      </el-table-column>
      <el-table-column align="center" label="状态">
        已发货
      </el-table-column>
      <el-table-column align="center" label="操作">
        <template slot-scope="scope">
          <router-link :to="'#' +scope.row.id">
            <el-button type="primary" size="small" icon="el-icon-edit">
              编辑
            </el-button>
          </router-link>
        </template>
      </el-table-column>
    </el-table>
    <pagination v-show="total>0" :total="total" :page.sync="listQuery.page" :limit.sync="listQuery.limit" @pagination="getList"></pagination>
  </div>
</template>
<script>
import Pagination from '@/components/Pagination'
import { fetchList } from '@/api/article'
export default {
  name: 'OrderCenter',
  components: { Pagination },
  data() {
    return {
      list: null,
      total: 0,
      listLoading: true,
      listQuery: {
        page: 1,
        limit: 20
      }
    }
  },
  created() {
    this.getList()
  },
  methods: {
    getList() {
      this.listLoading = true
      fetchList(this.listQuery).then(response => {
        this.list = response.data.items
        this.total = response.data.total
        this.listLoading = false
      })
    }
  }
}
</script>
