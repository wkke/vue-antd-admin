<template>
  <a-form @submit="handleSubmit" :autoFormCreate="(form) => this.form = form" class="form">
    <a-row class="form-row">
      <a-col :lg="6" :md="12" :sm="24">
        <a-form-item
          label="仓库名"
          fieldDecoratorId="repository.name"
          :fieldDecoratorOptions="{rules: [{ required: true, message: '请输入仓库名称', whitespace: true}]}"
        >
          <a-input placeholder="请输入仓库名称" />
        </a-form-item>
      </a-col>
      <a-col :xl="{span: 6, offset: 2}" :lg="{span: 8}" :md="{span: 12}" :sm="24">
        <a-form-item
          label="仓库域名"
          fieldDecoratorId="repository.domain"
          :fieldDecoratorOptions="{rules: [{ required: true, message: '请输入仓库域名', whitespace: true}, {validator: validate}]}"
        >
          <a-input addonBefore="http://" addonAfter=".github.io" placeholder="请输入"/>
        </a-form-item>
      </a-col>
      <a-col :xl="{span: 8, offset: 2}" :lg="{span: 10}" :md="{span: 24}" :sm="24">
        <a-form-item
          label="仓库管理员"
          fieldDecoratorId="repository.manager"
          :fieldDecoratorOptions="{rules: [{ required: true, message: '请选择管理员'}]}"
        >
          <a-select placeholder="请选择管理员">
            <a-select-option value="王同学">王同学</a-select-option>
            <a-select-option value="李同学">李同学</a-select-option>
            <a-select-option value="黄同学">黄同学</a-select-option>
          </a-select>
        </a-form-item>
      </a-col>
    </a-row>
    <a-row class="form-row">
      <a-col :lg="6" :md="12" :sm="24">
        <a-form-item
          label="审批人"
          fieldDecoratorId="repository.auditor"
          :fieldDecoratorOptions="{rules: [{ required: true, message: '请选择审批员'}]}"
        >
          <a-select placeholder="请选择审批员">
            <a-select-option value="王晓丽">王晓丽</a-select-option>
            <a-select-option value="李军">李军</a-select-option>
          </a-select>
        </a-form-item>
      </a-col>
      <a-col :xl="{span: 6, offset: 2}" :lg="{span: 8}" :md="{span: 12}" :sm="24">
        <a-form-item
          label="生效日期"
          fieldDecoratorId="repository.effectiveDate"
          :fieldDecoratorOptions="{rules: [{ required: true, message: '请选择生效日期'}]}"
        >
          <a-range-picker style="width: 100%" />
        </a-form-item>
      </a-col>
      <a-col :xl="{span: 8, offset: 2}" :lg="{span: 10}" :md="{span: 24}" :sm="24">
        <a-form-item
          label="仓库类型"
          fieldDecoratorId="repository.type"
          :fieldDecoratorOptions="{rules: [{ required: true, message: '请选择仓库类型'}]}"
        >
          <a-select placeholder="请选择仓库类型">
            <a-select-option value="公开">公开</a-select-option>
            <a-select-option value="私密">私密</a-select-option>
          </a-select>
        </a-form-item>
      </a-col>
    </a-row>
    <a-form-item v-if="showSubmit">
      <a-button htmlType="submit" >Submit</a-button>
    </a-form-item>
  </a-form>
</template>

<script>
import AForm from 'ant-design-vue/es/form/Form'
import AFormItem from 'ant-design-vue/es/form/FormItem'
import ACol from 'ant-design-vue/es/grid/Col'
import ARow from 'ant-design-vue/es/grid/Row'
import AInput from 'ant-design-vue/es/input/Input'
import ASelect from 'ant-design-vue/es/select/index'
import ADatePicker from 'ant-design-vue/es/date-picker'
import AButton from 'ant-design-vue/es/button/button'

const ASelectOption = ASelect.Option
const ARangePicker = ADatePicker.RangePicker

export default {
  name: 'RepositoryForm',
  props: ['showSubmit'],
  components: {AButton, ARangePicker, ASelectOption, ASelect, AInput, ARow, ACol, AFormItem, AForm},
  methods: {
    handleSubmit (e) {
      e.preventDefault()
      this.form.validateFields((err, values) => {
        if (!err) {
          console.log('Received values of form: ', values)
        }
      })
    },
    validate (rule, value, f) {
      if (value !== undefined && value !== 'iczer') {
        f('输入\'iczer\'试下？')
      }
      f()
    }
  }
}
</script>

<style lang="less" scoped>
  .form{
    .form-row{
      margin: 0 -8px
    }
    .ant-col-md-12,
    .ant-col-sm-24,
    .ant-col-lg-6,
    .ant-col-lg-8,
    .ant-col-lg-10,
    .ant-col-xl-8,
    .ant-col-xl-6{
      padding: 0 8px
    }
  }
</style>
