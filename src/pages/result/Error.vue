<template>
    <a-card :bordered="false">
      <result style="margin-bottom: 16px; margin-top: 48px" :is-success="false" :title="title" :description="description">
        <template slot="action">
          <a-button type="primary" >返回修改</a-button>
        </template>
        <div>
          <div style="fontSize: 16px; color: rgba(0, 0, 0, 0.85); fontWeight: 500; marginBottom: 16px">
            您提交的内容有如下错误：
          </div>
          <div style="margin-bottom: 16px">
            <a-icon type="close-circle-o" style="color: #f5222d; margin-right: 8px"/>
            您的账户已被冻结
            <a style="margin-left: 16px">立即解冻 <a-icon type="right" /></a>
          </div>
          <div>
            <a-icon type="close-circle-o" style="color: #f5222d; margin-right: 8px"/>
            您的账户还不具备申请资格
            <a style="margin-left: 16px">立即升级 <a-icon type="right" /></a>
          </div>
        </div>
      </result>
    </a-card>
</template>

<script>
import Result from '../../components/result/Result'
import ACard from 'ant-design-vue/es/card/Card'
import AIcon from 'ant-design-vue/es/icon/icon'
import AButton from 'ant-design-vue/es/button/button'
export default {
  name: 'Error',
  components: {AButton, AIcon, ACard, Result},
  data () {
    return {
      title: '提交失败',
      description: '请核对并修改以下信息后，再重新提交。'
    }
  }
}
</script>

<style scoped>

</style>
